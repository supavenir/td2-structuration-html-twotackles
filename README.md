[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/TlHh7BH_)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=20872465)
## Bloc 1 — Bases HTML • Structuration (TD2)
Durée indicative: 4 h+

---

### 🎯 Objectifs
- Structurer des contenus en HTML (titres, paragraphes, listes, liens, tableaux).
- Mettre en forme avec CSS (sélecteurs, typographie, mise en page simple).
- Publier vos travaux via GitHub Pages.
- Configurer un virtual host local pointant vers votre dossier de publications.
- Valider la qualité du code (HTML/CSS) avec les validateurs W3C.

---

### ✅ Pré-requis
- Compte GitHub actif.
- Connexion internet.
- Droits administrateur sur votre poste de travail.

---

### 📦 Référentiel (repository) et organisation
- Utilisez le repository associé à votre assignment GitHub Classroom.
- Travaillez en local puis commit/push régulièrement (au moins à la fin de chaque partie).
- Vérifiez et tenez compte des commentaires éventuels lors des code reviews.

Organisation des sources (pour ce TD):
- HTML: `docs/pages/td2/`
- CSS: `docs/assets/css/td2/`

Arborescence suggérée:
```
docs/
├─ index.html
├─ assets/
│  └─ css/
│     ├─ main.css
│     └─ td2/
│        ├─ mentions-legales.css
│        ├─ pate-a-crepes.css
│        └─ statuts-juridiques.css
└─ pages/
   └─ td2/
      ├─ mentions-legales-1.html
      ├─ mentions-legales-2.html
      ├─ mentions-legales-3.html
      ├─ pate-a-crepes.html
      └─ statuts-juridiques.html
```

Note: Les fichiers `.gitkeep` (vides) peuvent être utilisés pour forcer la présence de dossiers dans Git.

---

### 🌐 Publication avec GitHub Pages
- Dans votre repo: Settings → Pages.
- Source: branche `main`, dossier `/docs`.
- À chaque push modifiant `docs/`, un déploiement GitHub Pages est exécuté automatiquement (voir onglet Actions).

---

### 📚 Lectures (recommandées)
- [Bases HTML (structure sémantique, titres h1–h6, p, ul/ol, a, table…)](https://slamwiki2.kobject.net/web/html)
- [Bases CSS (sélecteurs, cascade, héritage, box model, typographie)](https://slamwiki2.kobject.net/web/css).
- [Débogage (DevTools)](https://slamwiki2.kobject.net/web/html/debug).
- [Autres supports (FR)](https://developer.mozilla.org/fr/docs/Learn/Getting_started_with_the_web/HTML_basics).
- [Entraînez-vous avec des exercices dédiés](https://aymeric-auberton.fr/academie/html/exercices).

---

### 🧪 Travaux à réaliser

#### 1) Pages Web et accueil du site (GitHub Pages)
- Créez un dossier `docs/` à la racine du repository (si absent).
- Ajoutez `docs/index.html` qui contient:
  - Un titre h1: « bloc1-SLAM ».
  - Un titre h2: « Documents ».
  - Une liste de liens vers les documents produits dans ce TD (voir sections 3–5).
- Créez/complétez `docs/assets/css/main.css`:
  - Définissez une Google Font (au choix) appliquée au `body`.
  - Appliquez une présentation spécifique aux titres.
- Vérifiez le rendu sur l’URL GitHub Pages une fois déployé.

Checklist:
- [ ] `index.html` présent, valide, lisible
- [ ] `main.css` chargé et appliqué
- [ ] Liens vers toutes les productions du TD

---

#### 2) Configuration d’un serveur HTTP (virtual host local)
- Modifiez la configuration de votre virtual host Apache local pour qu’il pointe sur le dossier `docs` de votre repository.
- Durcissez la configuration:
  - Masquez la version du serveur et du système.
  - Désactivez le listing des répertoires.

Exemple (à adapter à votre environnement):
```apache
<VirtualHost *:80>
    ServerName dev.local
    DocumentRoot "C:/chemin/vers/votre/repo/docs"
    <Directory "C:/chemin/vers/votre/repo/docs">
        AllowOverride All
        Options -Indexes
        Require all granted
    </Directory>
    ErrorLog  "logs/dev-error.log"
    CustomLog "logs/dev-access.log" combined
</VirtualHost>

# Dans httpd.conf ou conf globale
ServerSignature Off
ServerTokens Prod
```

À livrer dans votre repo (extraits/preuves):
- [ ] Extrait(s) de configuration avant/après
- [ ] Capture(s) ou sorties montrant la différence (headers, pages d’index, 403 sur listing, etc.)

---

#### 3) Structuration de texte, liens et Mentions légales
À partir du PDF « mentions-legales.pdf » fourni.

Version 1 — Structuration fidèle:
- Créez la structure HTML (doctype, lang, head, meta, title).
- Titre de la page: « Mentions légales ».
- Structurez le contenu avec des titres (h1/h2/h3…) et paragraphes.
- Créez les liens externes (ouverture dans un nouvel onglet).
- Fichiers:
  - HTML: `mentions-legales-1.html`
  - CSS: `mentions-legales.css`

Version 2 — Menu d’ancrage:
- Ajoutez en haut de page un menu (liste à puces) listant tous les titres de niveau 2 (Édition du site, Hébergement, …).
- Chaque entrée du menu pointe vers l’ancre correspondante dans la page.
- Fichier: `mentions-legales-2.html`

Version 3 — Navigation interne:
- Page principale: n’affiche que les titres de niveau 2.
- Chaque titre est un lien qui affiche la section correspondante (même page).
- Chaque « page de détail » permet de revenir à la page principale.
- Fichiers:
  - Page principale: `mentions-legales-3.html`
  - Dossiers/fichiers de détail nommés explicitement.

Bonnes pratiques:
- Sémantique consistante, attributs `id` clairs pour les ancres.
- Accessibilité: liens explicites, hiérarchie des titres correcte.

---

#### 4) Listes et mise en forme — « Pâte à crêpes »
À partir du PDF « pate-a-crepes.pdf » fourni.
- Créez la page `pate-a-crepes.html` avec une structure sémantique claire (titres, paragraphes, listes d’ingrédients/étapes).
- CSS dédié dans `pate-a-crepes.css`.
- Titre de la page: « Pâte à crêpes ».

---

#### 5) Tableaux — « Statuts juridiques »
À partir du PDF « statuts-juridiques.pdf » fourni.
- Créez la page `statuts-juridiques.html`.
- Titre: « Statuts juridiques ».
- Utilisez un tableau sémantique (caption, thead, tbody, th scope, etc.) pour présenter les informations.
- CSS dédié: `statuts-juridiques.css`.

---

#### 6) Détente avant le dîner — Sélecteurs CSS
- Entraînez-vous aux sélecteurs CSS (ex.: CSS Diner).
- Notez dans un court fichier Markdown ce que vous avez appris et 3–5 sélecteurs utiles avec exemples.
  - Suggestion: `docs/pages/td2/selecteurs-notes.md`

---

#### 7) Mise à jour de la page d’accueil
- Mettez à jour `docs/index.html` pour inclure des liens vers:
  - Mentions légales (versions 1, 2, 3)
  - Pâte à crêpes
  - Statuts juridiques
  - Notes sur les sélecteurs

Checklist:
- [ ] Tous les nouveaux documents sont accessibles depuis l’accueil
- [ ] Liens testés localement et en production (GitHub Pages)

---

#### 8) Vérifications (qualité)
- Validez vos pages HTML et CSS avec les validateurs W3C.
- Corrigez les erreurs et warnings éventuels.
- Contrôlez le rendu sur plusieurs navigateurs si possible.

À consigner:
- [ ] Captures ou rapports de validation
- [ ] Liste des corrections effectuées

---

### 🗂️ Récapitulatif des livrables
- `docs/index.html` mis à jour.
- `docs/pages/td2/mentions-legales-1.html`
- `docs/pages/td2/mentions-legales-2.html`
- `docs/pages/td2/mentions-legales-3.html` (+ éventuels sous-fichiers)
- `docs/pages/td2/pate-a-crepes.html`
- `docs/pages/td2/statuts-juridiques.html`
- Feuilles de style dédiées dans `docs/assets/css/td2/`
- Notes sur les sélecteurs: `docs/pages/td2/selecteurs-notes.md`
- Extraits de configuration Apache (avant/après) + preuves

---

### 🧭 Conseils pratiques
- Commits atomiques, messages clairs et descriptifs.
- Nommage explicite des fichiers et des `id` d’ancres.
- Structure sémantique avant la mise en forme.
- Réutilisez des classes CSS, limitez l’usage des ids pour le style.
- Testez localement puis sur GitHub Pages.
- Documentez vos choix (typographie, structure, accessibilité) en commentaires ou dans un court `README` de dossier.
