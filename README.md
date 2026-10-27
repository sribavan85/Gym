# Kern und Kraft

Kostenlose Fitness-App für zwei Ziele, die zusammen funktionieren: Muskeln aufbauen und Fett am Bauch abbauen.
Eine einzige HTML-Datei, läuft offline im Browser, speichert alles nur auf deinem Gerät. Kein Konto, kein Server, kein Abo.

## Was die App kann

- **Erstgespräch**: Alter, Größe, Gewicht, Ziel, Alltag, Trainingstage, Ausstattung. Daraus berechnet sie Grundumsatz (Mifflin-St Jeor), Verbrauch, ein moderates Kalorienziel (300 bis 500 kcal Defizit, mit sicherer Untergrenze) und ein Proteinziel (1,8 g pro kg Zielgewicht).
- **Trainingsplan**: Ganzkörper A/B bei 2 bis 3 Einheiten, Ober-/Unterkörper bei 4 Einheiten. Drei Varianten: Fitnessstudio, Zuhause mit Kurzhanteln, nur Körpergewicht. Jede Übung mit Sätzen, Wiederholungsbereich, Pause, Ausführungshinweis und Ausweichübung.
- **Check-in und Check-out**: ein Tipp beim Betreten des Studios, einer beim Verlassen. Dauer wird gemessen, beim Check-out wählst du mit einem Tipp, welche Einheit es war. Das reicht, um die Woche zu zählen.
- **Trainings-Logbuch (optional)**: Gewicht und Wiederholungen pro Satz, Sätze abhaken. Die App zeigt die letzte Leistung und schlägt die Steigerung vor (progressive Überlastung).
- **Dashboard**: Kennzahlen mit Sparklines (Gewicht, Training, Ruhepuls, Schlaf, HRV, Schritte), Gewichtskurve mit 7-Tage-Schnitt, Ziellinie, Tooltip und Zeitraum-Wahl, Kalorien- und Proteinringe, Wochenschnitte.
- **Apple Health und Oura**: Gewicht, Ruhepuls, HRV, Schlaf und Schritte kommen per iPhone-Kurzbefehl aus Apple Health (Oura schreibt seine Daten dorthin). Werte lassen sich auch von Hand eintragen.
- **Dark Mode**: standardmäßig dunkel, umschaltbar auf hell oder Geräteeinstellung.
- **Essen**: Kalorien und Protein pro Tag, Mahlzeiten-Vorlagen zum Antippen (vegetarisch, vegan oder alles, je nach Profil), Proteinquellen ohne Fleisch, Schritte.
- **Mahlzeit fotografieren**: In der auf claude.ai veröffentlichten Version schätzt Claude Kalorien, Protein und Bestandteile direkt aus dem Foto, über das eigene Claude-Konto und ohne Zusatzkosten. Die Zahlen lassen sich vor dem Eintragen anpassen. In anderen Versionen trägt ein Link der Form `#meal?n=NAME&kcal=600&p=35` eine im Chat geschätzte Mahlzeit ein.
- **Wöchentlicher Check-in**: bewertet Gewichtstrend, Training und Essen und dreht genau eine Stellschraube.
- **Sicherung**: Export und Import als JSON-Datei.

## So nutzt du sie, ohne einen Cent zu zahlen

**Option 1, sofort:** `index.html` herunterladen und im Browser öffnen. Funktioniert auch ohne Internet.

**Option 2, als App auf dem Handy (empfohlen):**

1. In diesem GitHub-Repo unter *Settings → Pages* als Quelle den Branch `main` und den Ordner `/ (root)` wählen. GitHub Pages ist kostenlos.
2. Nach ein bis zwei Minuten ist die App unter `https://sribavan85.github.io/gym/` erreichbar.
3. Die Adresse auf dem Handy öffnen und im Browser-Menü **Zum Home-Bildschirm** wählen. Danach startet sie wie eine normale App, auch offline.

## Apple Health und Oura anbinden (iPhone)

Eine Web-App darf Apple Health nicht direkt lesen. Ein Kurzbefehl kann das und schickt die Werte per Link an die App. Oura schreibt Schlaf, Ruhepuls und HRV nach Apple Health (Oura-App → Einstellungen → Apple Health → Schreiben erlauben), damit kommen die Ring-Daten auf demselben Weg an.

Der Link hat diese Form (Einheiten im Text stören nicht, die App liest nur die Zahl; Schlaf in Minuten oder Stunden wird automatisch erkannt):

```
https://<deine-adresse>/index.html#health?w=85,3&rhr=56&hrv=42&sleep=438&steps=8120
```

Kurzbefehl „Health senden“: je eine Aktion **Gesundheitsdaten suchen** für Gewicht, Ruheherzfrequenz und Herzfrequenzvariabilität (neuester Wert), für Schlafanalyse (Wert „Schlafend“, Startdatum nach gestern 18:00, dann **Statistiken berechnen** Summe) und für Schritte (heute, Summe). Zum Schluss **URL öffnen** mit dem Link, in dem die Platzhalter durch die Variablen ersetzt sind. Eine Automation „Tageszeit 9:00, sofort ausführen“ schickt die Werte dann jeden Morgen. Die Schritt-für-Schritt-Anleitung steht in der App unter *Mehr*.

## Check-in automatisch im Studio (iPhone)

Die McFIT-App bietet keine Schnittstelle für Besuche. Das iPhone kann den Check-in aber am Ort auslösen, ohne dass du etwas öffnest:

- `…/index.html#checkin` startet den Check-in
- `…/index.html#checkout` öffnet den Check-out

Kurzbefehle → Automation → **Ankommen** (Adresse des Studios, sofort ausführen) → **URL öffnen** mit dem Check-in-Link. Zweite Automation mit **Verlassen** und dem Check-out-Link.

Hinweis: Automationen öffnen den Link in Safari. Nutze die App entweder immer in Safari oder immer als installierte App, denn beide haben getrennten Speicher.

## Datenschutz

Alle Daten liegen im lokalen Speicher deines Browsers (`localStorage`). Nichts verlässt das Gerät. Wenn du Browserdaten löschst oder das Gerät wechselst, vorher unter *Mehr → Daten sichern* exportieren.

## Grenzen

Die App ist Coach, kein Arzt. Bei Erkrankungen, Medikamenten, Gelenkproblemen oder einem großen Abnahmeziel den Plan ärztlich abklären lassen.
