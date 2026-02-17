# LAB 3 : Observation du trafic HTTP(S) Android avec Burp Suite

## Contexte
- Émulateur Android utilisé pour un labo sûr  
- Objectif : observer le trafic HTTP/HTTPS  
- Cible : application ou site autorisé  

---

## 1. Préparer Burp Suite
- Lancer Burp Suite et créer un projet temporaire  
- Aller dans **Proxy → vérifier que Intercept is off**  
- Pourquoi : éviter de bloquer le trafic avant de configurer le proxy  

**Captures :**  
![Intercept Off](https://github.com/user-attachments/assets/a5a72ba5-ad30-445b-9838-81f205f85fe0)  
![Intercept Off](https://github.com/user-attachments/assets/47b1a4ba-704e-4d48-b8d8-7f88aa4fad7e)  

---

## 2. Vérifier le Proxy Listener
- Dans **Proxy → Settings / Proxy listeners**  
- Vérifier que le listener est activé (Enabled)  
- Noter : port `<PORT_PROXY>` et adresse d’écoute (Loopback / All interfaces)  

**Capture :**  
![Proxy Listener](https://github.com/user-attachments/assets/b3552eca-12bd-4a61-9977-6c5bf6bc3205)  

---

## 3. Trouver l’IP de la machine hôte
- Sur la machine hôte, récupérer l’adresse IPv4 utilisée pour le réseau du labo  
- Noter l’IP : `<IP_HOTE>`  

**Captures :**  
![IP Hôte](https://github.com/user-attachments/assets/c4d74d85-badb-4a87-a1c9-8ee9e723c93a) 
![IP Hôte](https://github.com/user-attachments/assets/1bbab50e-68e0-41c2-a7f1-05bec8553050)  
 
---

## 4. Configurer le proxy sur l’émulateur
- Paramètres Wi-Fi : détails du réseau → options avancées → Proxy : Manual  
- Renseigner :
  - Hostname : `<IP_HOTE>`  
  - Port : `<PORT_PROXY>`  

**Capture :**  
![Proxy Android](https://github.com/user-attachments/assets/01c96be2-886c-438f-a768-544bb0891188)  

---

## 5. Vérifier la capture dans Burp
- Naviguer sur une page autorisée dans l’émulateur  
- Dans **HTTP History**, observer :  
  - Méthode (GET/POST)  
  - URL  
  - Headers  
  - Cookies  

**Captures :**  
![Emulator](https://github.com/user-attachments/assets/01a24e78-dd7f-47dc-a08d-36ae5d64c880)  
![HTTP History](https://github.com/user-attachments/assets/8fc4b3d2-716e-4237-a3f9-5df84d52abba)  

---

## 6. Analyse d’une requête
- Onglet **Raw** : méthode, chemin, headers, cookies  
- Onglet **Inspector** : paramètres, cookies, headers structurés  
- Points à vérifier : données sensibles, tokens dans l’URL, cookies sécurisés  

**Capture :**  
![Analyse Requête](https://github.com/user-attachments/assets/72ccb73f-3170-4ce5-a477-2b4f0a874606)  

---

## 7. Interception contrôlée (optionnelle)
- Activer **Intercept** pour une courte démonstration  
- Rafraîchir une page : observer la requête en attente  
- Désactiver l’interception ensuite  

**Captures :**  
![Intercept Active](https://github.com/user-attachments/assets/a6d2efa3-5202-4c33-a449-d4120db09cda)  
![Requête en attente](https://github.com/user-attachments/assets/742f986d-5cce-4fec-9a90-51d49c811f23)  

---

## 8. HTTPS et certificat CA
- Installer le certificat CA uniquement dans l’émulateur pour HTTPS  
- Retirer le certificat après le labo  
- Ne jamais installer sur un appareil personnel  

**Captures :**  
![Certificat CA](https://github.com/user-attachments/assets/3cf6c53a-e57e-40fa-9f0d-5b0ed21dbe08)  
![Certificat CA](https://github.com/user-attachments/assets/b27c1d3a-836c-486c-8a78-841bd3653bab)  
![Certificat CA](https://github.com/user-attachments/assets/a0ae3c2d-77f8-4dcc-b4df-48b091adb54a)  

---

## 9. Bonnes pratiques
- Minimiser les données envoyées côté client  
- Ne pas mettre de tokens dans l’URL  
- Utiliser HTTPS et sécuriser les cookies (Secure, HttpOnly, SameSite)  
- Documenter toutes les observations et captures  

---

## 10. Nettoyage
- Remettre le proxy à **None** dans l’émulateur  
- Retirer le certificat CA  
- Fermer Burp et conserver uniquement les preuves nécessaires  
