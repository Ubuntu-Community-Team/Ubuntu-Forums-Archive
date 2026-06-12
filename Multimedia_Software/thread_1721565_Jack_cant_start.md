---
title: "Jack cant start"
date: 2011-04-04
forum: Multimedia Software
---

### Post by Dagostin on 2011-04-04
23:59:30.001 Steckfeld deaktiviert. 23:59:30.168 Statistik zurückgesetzt. Cannot connect to server socket err = Verbindungsaufbau abgelehnt Cannot connect to server socket jack server is not running or cannot be started 23:59:30.197 Schaubild der ALSA-Verbindungen geändert. 23:59:30.482 ALSA-Verbindung geändert. 23:59:31.857 Start-Skript... 23:59:31.858 artsshell -q terminate Cannot connect to server socket err = Verbindungsaufbau abgelehnt Cannot connect to server socket jack server is not running or cannot be started sh: artsshell: not found 23:59:32.260 Start-Skript beendet mit Rückgabewert = 32512. 23:59:32.261 JACK startet... 23:59:32.261 usr/bin/jackd -dalsa -d/dev/audio -r44100 -p1024 -n2 23:59:32.271 Konnte JACCK nicht starten. 23:59:37.612 JACK wurde angehalten mit Rückgabewert = 255. 23:59:37.613 Nach-Herunterfahr-Skript... 23:59:37.614 killall jackd jackd: Kein Prozess gefunden 23:59:38.035 Nach-Herunterfahr-Skript beendet mit Rückgabewert = 256.     this is was i get when i try to start jack jack was already installed from the beginning i tried to change the server path but didnt work i dont have this much understanding of such matters can you please help me?

---

### Post by Dagostin on 2011-04-04
after i reinstalled i got this 00:13:23.775 Steckfeld deaktiviert. 00:13:23.885 Statistik zurückgesetzt. JackSocketClientChannel read fail Cannot open qjackctl client 00:13:28.959 Schaubild der ALSA-Verbindungen geändert. 00:13:29.332 ALSA-Verbindung geändert. 00:16:56.707 Start-Skript... 00:16:56.707 artsshell -q terminate Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden Cannot connect to server socket jack server is not running or cannot be started sh: artsshell: not found 00:16:57.109 Start-Skript beendet mit Rückgabewert = 32512. 00:16:57.110 JACK startet... 00:16:57.110 usr/bin/jackd -r -dalsa -d/dev/audio -r44100 -p1024 -n2 00:16:57.120 Konnte JACCK nicht starten. 00:16:58.884 JACK wurde angehalten mit Rückgabewert = 255. 00:16:58.885 Nach-Herunterfahr-Skript... 00:16:58.887 killall jackd jackd: Kein Prozess gefunden 00:16:59.297 Nach-Herunterfahr-Skript beendet mit Rückgabewert = 256.

---

