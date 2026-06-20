# Quiz App

**Copyright © 2026 Sven Riedel. Alle Rechte vorbehalten.**
Proprietäre Software – Nutzung, Vervielfältigung und Weitergabe nur mit ausdrücklicher schriftlicher Genehmigung des Urhebers.

---

## Beschreibung

Eine vollständig in sich geschlossene, browserbasierte Quiz-App für Gruppen und Events.

---

## Features

### Themes
Die App unterstützt vier wählbare Themes, die Farben, Hintergrund, Partikeleffekte und Standardtitel anpassen:

| Theme | Icon | Partikeleffekte |
|---|---|---|
| Weihnachten | 🎄 | ❄ ❅ ❆ ✦ |
| Ostern | 🐣 | 🌸 🌷 🥚 🐣 🌼 |
| Halloween | 🎃 | 🎃 🦇 👻 🕷️ |
| Sport | 🏆 | ⚽ 🏀 🏆 ⭐ |

Das Theme wird entweder aus dem geladenen Fragenkatalog (`.json`) übernommen oder kann jederzeit über **⚙ Einstellungen → 🎨 Optionen** gewechselt werden.

### Spielmodi
Vor dem Start wird neben der Teamanzahl auch der Spielmodus festgelegt:

- **👥 Team-Modus** – Mehrere Teams können bei derselben Frage Punkte erhalten; der Spielleiter vergibt sie nach Anzeige der Antwort manuell per Klick an beliebig viele Teams (jedes Team max. einmal pro Frage).
- **⚔️ VS-Modus** – Nur ein Team kann pro Frage punkten. Antwortet das zuerst gewählte Team falsch, gibt es Punktabzug und die Frage wird für die übrigen Teams zur **Weitergabe** mit halben Punkten freigegeben. Ein eingeblendetes Mode-Badge zeigt jederzeit den aktiven Modus an.

### Moderator-Antwortvorschau
Im **VS-Modus** öffnet sich automatisch ein separates Browser-Popup-Fenster nur für den Spielleiter. Über den Button **👁 Antwort prüfen** kann die richtige Antwort (inkl. Kategorie und aktuellem Punktwert) dort eingesehen werden, ohne sie auf dem für alle sichtbaren Hauptbildschirm/Beamer preiszugeben.

### Fragentypen
Jede Frage kann einen der folgenden Inhaltstypen haben:

- **Text** – klassische Frage als reiner Text, optional mit zusätzlichem Antwort-Medium (Bild/Video/Audio/YouTube), das erst beim Aufdecken der Antwort angezeigt wird
- **Bild** – lokale Bilddatei hochladen oder URL eingeben (optional **verpixelt** darstellbar; beim Aufdecken der Antwort wird automatisch das Originalbild eingeblendet); Bilder lassen sich per Klick in einer Vollbild-Lightbox vergrößern
- **Audio** – lokale Audiodatei mit eigenem Play/Pause-Button; alternativ eine YouTube-URL für reine Musikwiedergabe ohne sichtbares Video
- **Video** – lokale Videodatei mit nativen Steuerelementen, Lautstärke richtet sich nach der globalen Video-Lautstärke
- **YouTube** – YouTube-Link direkt im Video- oder Audio-Feld eingeben; die YouTube IFrame API wird dabei erst bei Bedarf (Klick auf Play) nachgeladen. Native YouTube-Steuerelemente sind ausgeblendet, stattdessen gibt es einen eigenen Vollbild-Button; optional lassen sich Startzeit und Wiedergabedauer pro Frage begrenzen

Bei Bild-, Video-, Audio- und YouTube-Fragen lässt sich zusätzlich ein optionaler **Fragetext** hinterlegen, der oberhalb des Mediums als kurze Zusatzinfo eingeblendet wird (z. B. ein Hinweis oder eine Teilfrage).

### Spielablauf
- Bis zu **10 Teams** spielen gleichzeitig, beliebig viele Kategorien sind möglich
- Teamnamen werden vor dem Spielstart individuell vergeben
- Das **Spielbrett** zeigt Kategorien als Spalten und Punktwerte als Zeilen
- Geklickte Felder öffnen die Frage in einem Modal-Fenster
- Nach Anzeige der Antwort vergibt der Spielleiter Punkte – die Vergabelogik unterscheidet sich je nach Team- oder VS-Modus (siehe oben)
- Bereits beantwortete Felder werden ausgeblendet (stark transparent dargestellt und nicht mehr anklickbar)
- Die **Punkteanzeige** am unteren Rand hebt ein Team kurz golden hervor, sobald es Punkte erhält oder verliert
- Sobald alle Felder gespielt wurden, erscheint automatisch eine **Sieger-Anzeige** mit Feuerwerk-Animation, Siegerkrone, Podium für die Top 3 (🥇🥈🥉) und Unentschieden-Erkennung

### Punkte-Multiplikatoren
Multiplikatoren können so konfiguriert werden, dass sie nach einem bestimmten Prozentsatz der gespielten Fragen automatisch aktiviert werden (z. B. ×2 nach 30 % der Fragen). Mehrere Multiplikatoren stapeln sich multiplikativ: 2× nach 30 % und 4× nach 60 % ergeben ab 60 % insgesamt 8× Basispunkte.

### Timer
Jede Punktestufe erhält einen Standard-Timer (in Sekunden), der pro einzelner Frage überschrieben werden kann. Die Lautstärke des Timer-Tons sowie die Lautstärken für Video- und Musikwiedergabe sind separat einstellbar.

---

## Einrichtung & Bedienung

### Start
1. https://rdl-gaming.github.io/RDL-Gaming-Trivia-Quiz/ im Browser öffnen
2. Fragenkatalog als `.json`-Datei laden (beim Neustart eines bestehenden Spiels kann alternativ ein bereits im Speicher vorhandener Katalog weiterverwendet werden)
3. Anzahl der Teams (1–10) und Spielmodus (Team oder VS) wählen
4. Teamnamen eingeben
5. Quiz starten

Das Theme wird dabei automatisch aus dem geladenen Katalog übernommen und kann jederzeit später in den Einstellungen geändert werden.

### Settings-Panel
Über den Button **⚙ Einstellungen** (oben rechts im Quiz) öffnet sich das Settings-Panel. In der Kopfzeile stehen jederzeit folgende Aktionen zur Verfügung:

- **🔁 Fragen neu starten** – setzt Punkte und Spielfortschritt zurück, Fragen/Kategorien/Teams bleiben erhalten
- **🎮 Spiel neu starten** – setzt das gesamte Spiel zurück und führt zur Katalog-/Teamauswahl
- **📥 Import** / **📤 Export** (siehe unten)

Darunter gliedert sich das Panel in vier Reiter:

**📝 Fragen**
Legt zunächst über die **Fragenstruktur** fest, wie viele Punktestufen es gibt und welche Punkte- und Standard-Timerwerte pro Stufe gelten (Stufen lassen sich hinzufügen oder löschen). Darunter werden alle Fragen und Antworten bearbeitet: Fragetyp wählen, Medien hochladen oder per URL einbinden, Verpixelung umschalten, optionalen Fragetext hinterlegen, Start-/Endzeit für Video-/Audio-/YouTube-Inhalte setzen, optionales Antwort-Medium hinterlegen und Timer pro Frage individuell setzen.

**📁 Kategorien**
Kategorien anlegen, umbenennen, mit Emoji versehen, farblich anpassen oder löschen.

**🎨 Optionen**
- Theme wechseln
- Quiz-Titel anpassen
- Punkte-Multiplikatoren verwalten
- Lautstärke für Timer-Ton, Video und Musik separat einstellen

**📑 Rechtliches**
Impressum, Datenschutzerklärung, Lizenz und Drittanbieter-Hinweise direkt als schließbares Popup aufrufen (siehe Abschnitt „Rechtliche Hinweise“)

### Import / Export
- **Export:** Speichert den gesamten Spielstand als `.json`-Datei – Fragen und Antworten inkl. eingebetteter Medien, Kategorien, Punkte-/Timer-Stufen, Theme, Quiz-Titel, Multiplikatoren und Lautstärke-Einstellungen. In Chrome/Edge öffnet sich dafür ein nativer „Speichern unter"-Dialog mit einem aus dem Quiz-Titel abgeleiteten Dateinamen; in Firefox/Safari erfolgt ein klassischer Download.
- **Import:** Lädt eine zuvor exportierte `.json`-Datei und stellt den vollständigen Stand wieder her

---

## Datenspeicherung

Der aktuelle Spielstand, Fragen und Einstellungen werden automatisch im **localStorage** des Browsers gesichert. Änderungen im Settings-Panel werden nach 1 Sekunde Inaktivität automatisch gespeichert. Beim Schließen des Panels wird zusätzlich sofort gespeichert.

> **Hinweis:** Der localStorage ist browserspezifisch. Für dauerhafte Sicherung bitte regelmäßig exportieren.

---

## Drittanbieter-Hinweise

| Komponente | Lizenz |
|---|---|
| Mountains of Christmas, Playfair Display, Nunito (Google Fonts) | SIL Open Font License 1.1 (OFL) |
| YouTube IFrame API | Proprietärer Dienst von Google LLC – [Nutzungsbedingungen](https://www.youtube.com/t/terms) |

Weitere Details unter **⚙ Einstellungen → 📑 Rechtliches → ℹ️ Drittanbieter-Hinweise** einsehbar.

---

## Technische Voraussetzungen

- Moderner Browser (Chrome, Firefox, Edge, Safari)
- Internetverbindung nur für Google Fonts und YouTube-Einbettung erforderlich
- Keine Installation, kein Server, keine Build-Tools

## Lizenz

Copyright (c) 2026 Sven Riedel. Alle Rechte vorbehalten.
Proprietäre Software – siehe **⚙ Einstellungen → 📑 Rechtliches → 📜 Lizenz** für vollständige Bedingungen.

---

## Rechtliche Hinweise

**⚙ Einstellungen → 📑 Rechtliches**, dort:
- **📄 Impressum**
- **🔒 Datenschutzerklärung**
- **📜 Lizenz**
- **ℹ️ Drittanbieter-Hinweise**

Ein Klick auf einen der Buttons öffnet die jeweilige Information als schließbares Popup innerhalb der App.
