# ☀️ Le Soleil Italien — Liste des tâches

Application web collaborative pour gérer les tâches quotidiennes du restaurant, synchronisée en temps réel entre tous les membres de l'équipe.

---

## Fonctionnalités

- ✅ Cocher/décocher les tâches en un clic
- 👤 Affichage du prénom et de l'heure pour chaque tâche effectuée
- 🔄 Synchronisation en temps réel (Firebase) — tous les appareils se mettent à jour instantanément
- 📊 Barre de progression et compteur de tâches
- 🔃 Tri automatique : tâches à faire en haut, tâches terminées en bas
- 🔁 Bouton "Tout réinitialiser" pour repartir à zéro
- 🟢 Indicateur de connexion live

---

## Technologies utilisées

- HTML / CSS / JavaScript (vanilla)
- [Firebase Realtime Database](https://firebase.google.com/products/realtime-database) — stockage et sync en temps réel
- [Google Fonts](https://fonts.google.com/) — DM Serif Display + DM Mono
- Hébergement : [GitHub Pages](https://pages.github.com/)

---

## Installation

### 1. Cloner le repo

```bash
git clone https://github.com/TON_NOM/soleil-tasks.git
cd soleil-tasks
```

### 2. Configurer Firebase

1. Va sur [console.firebase.google.com](https://console.firebase.google.com)
2. Crée un projet → active **Realtime Database**
3. Dans ⚙️ **Paramètres du projet** → **Ajouter une app Web** → copie la config
4. Dans `index.html`, remplace la valeur `databaseURL` par ton URL Firebase :

```js
const firebaseConfig = {
    databaseURL: "https://TON-PROJET.firebaseio.com"
};
```

### 3. Règles de sécurité Firebase

Dans la console Firebase → **Realtime Database → Règles**, applique :

```json
{
  "rules": {
    ".read": "now < 1782684000000",
    ".write": "now < 1782684000000"
  }
}
```

> ⚠️ Ces règles expirent le **29 juin 2026**. Pense à les renouveler avant cette date.

---

## Déploiement sur GitHub Pages

1. Crée un repo GitHub (ex: `soleil-tasks`)
2. Dépose le fichier `index.html`
3. Va dans **Settings → Pages → Branch: main** → Save
4. Ton lien sera disponible à : `https://TON_NOM.github.io/soleil-tasks`

---

## Utilisation

- À la première visite, chaque membre entre son **prénom** — il sera mémorisé sur l'appareil
- Un clic sur une tâche la coche et affiche le prénom + l'heure
- Le prénom est modifiable à tout moment via l'icône 👤 en haut à droite
- Les tâches terminées passent automatiquement en bas de liste

---

## Structure du projet

```
soleil-tasks/
├── index.html   # Application complète (HTML + CSS + JS)
└── README.md    # Ce fichier
```

---

## Données Firebase

Les tâches sont stockées sous la clé `/tasks` avec la structure suivante :

```json
{
  "tasks": {
    "poussiere":  { "done": true,  "who": "Marie", "at": "09:15" },
    "serpillere": { "done": false, "who": null,    "at": null },
    "terrasse":   { "done": false, "who": null,    "at": null },
    "vin":        { "done": true,  "who": "Lucas", "at": "10:02" }
  }
}
```
