# Studio Lyric Video — Contexte du projet

## C'est quoi
Outil web pour créer une lyric video YouTube à partir d'un MP3, d'une cover et de paroles.
Tout se passe dans le navigateur (aucun envoi sur internet, pas de watermark).

- **Site en ligne** : https://osvalt16.github.io/studio-lyric-video/
- **Repo** : https://github.com/osvalt16/studio-lyric-video
- **Fichier unique** : `index.html` (HTML + CSS + JS, aucune dépendance)

## Fonctionnalités
1. **Étape 1** — chargement du MP3/WAV, de la cover, titre, artiste, résolution (1080p / 720p / Shorts 9:16)
2. **Étape 2** — paroles : une ligne de texte = une ligne à l'écran
   - Répartition automatique sur la durée de la chanson dès la saisie
   - Support du format **LRC** : `[m:ss.s] texte` → synchro exacte
3. **Étape 3** — synchro manuelle par tap (bouton ou Espace), compensation du temps de réaction (0,15 s), timings modifiables, décalage global ±0.2s/±0.5s
4. **Étape 4** — aperçu canvas temps réel (cover floutée en fond, équaliseur, barre de progression) et export WebM (MediaRecorder, 8 Mbps, enregistrement en temps réel)

## Historique des corrections
- Fix synchro : lignes non tapées traitées comme t=0 (l'aperçu affichait la dernière ligne)
- Fix : tap ignoré si l'audio est en pause, anti-répétition de la touche Espace
- Ajout : affichage auto des paroles sans synchro manuelle obligatoire
- Ajout : support LRC pour coller des paroles déjà synchronisées

## Notes techniques
- L'export sort en WebM ; pour MP4 : `ffmpeg -i video.webm video.mp4`
- Le graphe audio (AudioContext → analyser → destination + MediaStreamDestination) est créé au premier play
- Chanson de référence : « Feu interdit » (3:37) — paroles synchronisées dans `Feu interdit - paroles synchronisees.txt` (Téléchargements)
