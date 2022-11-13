# Android Backup mit adb

Um ein Backup von allen Daten auf dem Android zu machen, gibt es eine sehr schnelle Möglichkeit mit den _adb Tools_. Dazu wird das Handy per USB an einen PC angeschlossen. Bei diesem Backup werden alle Dateien auf den PC kopiert und die Ordner auf dem Android geleert. Du hast dann also null Fotos, null Musik und null Dokumente auf dem Android. Doch Achtung: Profis können auch gelöschte Daten wiederherstellen. Doch Ottilie Normalverbraucherin kann das nicht, zumindest nicht ohne weitere Kenntnisse. 

Das Backup ist eine gute Gelegenheit, mal Tabula Rasa auf deinem Handy zu machen und wieder Platz zu schaffen.

Das Backup machst du mit der ADB, der Android Debug Bridge.

Hinweis: Du kannst mit dem ADB deinem Android ernsthafte Schäden zufügen. Bitte benutze diese Anleitung nur, wenn du dir absolut sicher bist, was sie tut und du dir im klaren darüber bist, dass du eigenverantwortlich handelst. Nur du allein klickst auf etwas und machst etwas, nur du allein bist für dein Handeln verantwortlich.

Fangen wir an.

Lade dir die [ADB Tools](https://developer.android.com/studio/releases/platform-tools) auf deinen PC runter.

Die nachfolgende Anleitung ist für Windows-Benutzende geschrieben.

Lies die Bedingungen und Konditionen der ADB Tools und bestätige sie.

---

![Anleitung Bild 000a](img/anleitung_android-backup_000a.jpg)

---

Wenn du einverstanden bist, mache einen Haken an *I have read and agree with the above terms and conditions* und klick auf **Download Android SDK Platform-Tools for Windows**.

---

![Anleitung Bild 000b](img/anleitung_android-backup_000b.jpg)

---

Drücke in deinem Browser auf der Tastatur **STRG + J**. Es öffnet sich ein Fenster, welches deine Downloads zeigt. Klick mit einem Rechtsklick auf die platform-tools. Klick auf **In Ordner anzeigen** (das ist bei jedem Browser etwas unterschiedlich)

---

![Anleitung Bild 000c](img/anleitung_android-backup_000c.jpg)

---

Diese Datei befindet sich in deinem Download-Verzeichnis.

---

![Anleitung Bild 000d](img/anleitung_android-backup_000d.jpg)

---

Übrigens: Eine .zip-Datei ist ein Archiv, quasi wie ein Koffer. Und aus diesem Koffer werden gleich die Dateien entpackt. Klicke mit einem Rechtsklick auf die Datei. Aus dem Kontextmenü wählst du nun **Alle extrahieren...** aus. Nun wirst du gefragt, wohin du die Datei extrahieren möchtest. Klicke auf **Extrahieren**.

---

![Anleitung Bild 000e](img/anleitung_android-backup_000e.jpg)

---

Hier befindet sich nun der Ordner _platform-tools_. 

---

![Anleitung Bild 000f](img/anleitung_android-backup_000f.jpg)

---

Klicke unterhalb vom Ordner mit einem Rechtsklick in die leere Fläche. Das Kontextmenü öffnet sich. Wähle **Neu ► Textdokument**. Das Textdokument ist blau markiert. Klicke einmal neben die Datei irgendwo auf die leere Fläche. Doppelklick dann auf das Textdokument. Es öffnet sich der Editor.

---

![Anleitung Bild 000g](img/anleitung_android-backup_000g.jpg)

---

Markiere folgenden Code mit der Maus, klick Rechtsklick ► Kopieren und im Textdokument dann Rechtsklick ► Einfügen.

---

<pre>
@echo off
cls
echo Los geht es. Druecke eine Taste.
pause >nul
cd platform-tools
::Verbindung generieren
adb logcat -c

echo ....................Hole DCIM....................
adb pull "/storage/emulated/0/DCIM/" ../
adb shell rm -rf /storage/emulated/0/DCIM/
adb shell mkdir /storage/emulated/0/DCIM/
echo ...ok.

echo ....................Hole Documents....................
adb pull "/storage/emulated/0/Documents/" ../
adb shell rm -rf /storage/emulated/0/Documents/
adb shell mkdir /storage/emulated/0/Documents/
echo ...ok.

echo ....................Hole Download....................
adb pull "/storage/emulated/0/Download/" ../
adb shell rm -rf /storage/emulated/0/Download/
adb shell mkdir /storage/emulated/0/Download/
echo ...ok.

echo ....................Hole Movies....................
adb pull "/storage/emulated/0/Movies/" ../
adb shell rm -rf /storage/emulated/0/Movies/
adb shell mkdir /storage/emulated/0/Movies/
echo ...ok.

echo ....................Hole Music....................
adb pull "/storage/emulated/0/Music/" ../
adb shell rm -rf /storage/emulated/0/Music/
adb shell mkdir /storage/emulated/0/Music/
echo ...ok.

echo ....................Hole Pictures....................
adb pull "/storage/emulated/0/Pictures/" ../
adb shell rm -rf /storage/emulated/0/Pictures/
adb shell mkdir /storage/emulated/0/Pictures/
echo ...ok.

echo ....................Hole Podcasts....................
adb pull "/storage/emulated/0/Podcasts/" ../
adb shell rm -rf /storage/emulated/0/Podcasts/
adb shell mkdir /storage/emulated/0/Podcasts/
echo ...ok.

echo ....................Hole Recordings....................
adb pull "/storage/emulated/0/Recordings/" ../
adb shell rm -rf /storage/emulated/0/Recordings/
adb shell mkdir /storage/emulated/0/Recordings/
echo ...ok.

echo ....................Hole Ringtones....................
adb pull "/storage/emulated/0/Ringtones/" ../
adb shell rm -rf /storage/emulated/0/Ringtones/
adb shell mkdir /storage/emulated/0/Ringtones/
echo ...ok.


echo ....................Syslogs loeschen....................
adb logcat -c

echo ...ok.
::Verbindung beenden
adb kill-server
cd ..
echo Fertig. Bitte eine Taste druecken.
pause >nul
</pre> 

---

![Anleitung Bild 000h](img/anleitung_android-backup_000h.jpg)

---

Klicke auf **Datei ► Speichern unter...** 

---

![Anleitung Bild 000i](img/anleitung_android-backup_000i.jpg)

---

Trage bei Dateiname **"copy.bat"** ein. Achte darauf, die Anführungszeichen zu machen! Klicke dann auf **Speichern**.

---

![Anleitung Bild 000i](img/anleitung_android-backup_000j.jpg)

---

Jetzt hast du also den Ordner _platform-tools_ eine Datei namens _copy.bat_ und _Neues Textdokument.txt_. 

---

![Anleitung Bild 000k](img/anleitung_android-backup_000k.jpg)

---

Das Textdokument kannst du löschen. Klicke das Textdokument an, drücke auf deiner Tastatur **SHIFT + ENTF** und bestätige den Löschen-Dialog mit **Ja**.

---

![Anleitung Bild 000k](img/anleitung_android-backup_000l.jpg)

---

Schließe nun dein Handy per USB-Kabel an deinen PC an, am besten an einen USB 2.0 Anschluss. Gehe in die Einstellungen deines Handys, in dem du mit einem Finger von oben nach unten wischt und das Zahnrad-Symbol drückst.

---

![Anleitung Bild 001](img/anleitung_android-backup_001.jpg)

---

Scrolle nun so weit hinab, bis dort »Über das Telefon« steht. Klicke dort drauf.

---

![Anleitung Bild 004](img/anleitung_android-backup_004.jpg)

---

Scroll runter und klicke **8 mal** auf **Build-Nummer**. Jetzt hast du die **Entwickleroptionen** frei geschaltet.

---

![Anleitung Bild 005](img/anleitung_android-backup_005.jpg)

---

Gehe im Menü zurück zum Punkt **System**. Dort gibt es nun die **Entwickleroptionen**. Klicke da drauf.

---

![Anleitung Bild 007](img/anleitung_android-backup_007.jpg)

---

Der Schalter für **Entwickleroptionen verwenden** ist **aktiviert**.

---

![Anleitung Bild 008](img/anleitung_android-backup_008.jpg)

---

Wo du schon mal hier bist, kannst du auch noch etwas nützliches einstellen. Scroll runter zu **Mobile Datennutzung immer aktiviert**.

---

![Anleitung Bild 009](img/anleitung_android-backup_009.jpg)

---

Deaktiviere den Schalter. Ab jetzt hast du eine wesentlich längere Akkulaufzeit. Denn mobile Daten sind erst dann aktiviert, wenn du es willst und nicht, wenn dein Handy das für richtig hält.

---

![Anleitung Bild 010](img/anleitung_android-backup_010.jpg)

---

Scroll weiter runter zu **USB-Debugging**. Aktiviere den Schalter.

---

![Anleitung Bild 011](img/anleitung_android-backup_011.jpg)

---

Eine Warnmeldung poppt auf. Lies sie durch und bestätige mit **OK**.

---

![Anleitung Bild 012](img/anleitung_android-backup_012.jpg)

---

Nun siehst du eine Informationsnachricht ganz oben auf deinem Bildschirm. **USB-Debugging ist aktiviert**.

---

![Anleitung Bild 013](img/anleitung_android-backup_013.jpg)

---

Jetzt geht es los. Dein Handy ist mit dem PC verbunden. Starte nun die **copy.bat** in dem Ordner, den du vorhin auf deinem PC erstellt hast. Folge den Anweisungen auf deinem Bildschirm am PC. Nun wirst du gefragt, ob du das **USB-Debugging zulassen** möchtest. Bestätige mit **ERLAUBEN**.

---

![Anleitung Bild 015](img/anleitung_android-backup_015.jpg)

---

Nun rattert das Backup-Script durch dein Handy durch. Hinweis: Manchmal kann es lange dauern, dann steht dort: _Building File list_. Warte unbedingt ab! Zieh nicht am Kabel! Lass das Handy in Ruhe! Lass es einfach ganz in Ruhe durchlaufen. Sonst könnten Dateien beschädigt werden.

---

Nachdem in der **copy.bat** steht: **fertig.** und du eine Taste gedrückt hast, schließt sich das Script automatisch. Dein Backup ist dann fertig. Du kannst das Handy wieder vom Kabel entfernen. Gehe wieder in die Entwickleroptionen. (Einstellungen ► System ► Entwickleroptionen).

---

![Anleitung Bild 016](img/anleitung_android-backup_016.jpg)

---

**Deaktiviere** den Regler **USB-Debugging**.

---

![Anleitung Bild 017](img/anleitung_android-backup_017.jpg)

---

### Zusammenfassung:

Du hast dir Entwickler-Tools für dein Android heruntergeladen. Du hast eine Batch-Datei in Windows erstellt, die automatisch deine Daten vom Handy herunterläd und die Ordner leert. Du hast die Entwickleroptionen im Handy frei geschaltet und USB-Debugging aktiviert. Das erstellte Script hat die Daten auf deinen PC kopiert und die Ordner auf dem Handy geleert (technisch korrekt: nachdem die Daten heruntergeladen wurden, wurden die Ordner auf dem Handy gelöscht und neue Ordner mit gleichem Namen erstellt). Danach hast du das USB-Debugging wieder deaktiviert.

Du hast nun die Daten auf dem PC, aber nicht mehr auf dem Handy.

Hinweis: Gelöscht ist nicht gelöscht. Auch wenn Daten gelöscht werden (am PC oder auf dem Handy), sind sie nicht weg: Sie stehen dem System »zur Überschreibung bereit«. Doch so lange sie nicht überschrieben werden, lassen sie sich auch wieder herstellen. Das Backup-Script, das du hier verwendet hast, verschafft dir wieder Platz auf dem Handy. Es hindert Ottilie Ottonormalverbraucherin daran, falls dein Handy _abhanden_ kommen sollte, Daten auf deinem Handy zu finden. Technisch versierte Menschen können aber deine gelöschten Bilder und Dokumente und andere Daten wieder herstellen. Verlass dich also nicht auf das Backup-Script.
