---
title: "Echo bug after upgrade to 20.04"
date: 2020-11-17
forum: Multimedia Software
---

### Post by realjkh on 2020-11-17
Hi,

since I upgraded to 20.04 the system has a strange sound bug, meaning if I play an audio (Internet Video, internal mp3 ecetera) sometimes parts of the output is played double, like echoed.

Here is some terminal output:

```

ThisUser@ThisUser-HP-Notebook:~$ cat /proc/asound/cards 
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf0560000 irq 38
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xf0564000 irq 39
ThisUser@ThisUser-HP-Notebook:~$ aplay /usr/share/sounds/alsa/Front_Center.wav 
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono
ThisUser@ThisUser-HP-Notebook:~$ aplay /usr/share/sounds/alsa/Front_Center.wav 
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono
ThisUser@ThisUser-HP-Notebook:~$ aplay /usr/share/sounds/alsa/Front_Center.wav 
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono
ThisUser@ThisUser-HP-Notebook:~$ aplay /usr/share/sounds/alsa/Front_Center.wav 
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono
Unterlauf!!! (mindestens 1207,630 ms)
ThisUser@ThisUser-HP-Notebook:~$ sudo aplay /usr/share/sounds/alsa/Front_Center.wav 
[sudo] Passwort für ThisUser: 
ALSA lib pcm_dmix.c:1089:(snd_pcm_dmix_open) unable to open slave
aplay: main:830: Fehler beim Öffnen des Gerätes: Datei oder Verzeichnis nicht gefunden
ThisUser@ThisUser-HP-Notebook:~$ sudo addgroup BENUTZERNAME audio 
addgroup: Der Benutzer »BENUTZERNAME« existiert nicht.
ThisUser@ThisUser-HP-Notebook:~$ sudo addgroup ThisUser audio
Benutzer »ThisUser« wird der Gruppe »audio« hinzugefügt …
Benutzer ThisUser wird zur Gruppe audio hinzugefügt.
Fertig.
ThisUser@ThisUser-HP-Notebook:~$ echo normal:; aplay -l; echo sudo:; sudo aplay -l 
normal:
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: HDMI [HDA ATI HDMI], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Generic [HD-Audio Generic], Gerät 0: ALC3227 Analog [ALC3227 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
sudo:
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: HDMI [HDA ATI HDMI], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Generic [HD-Audio Generic], Gerät 0: ALC3227 Analog [ALC3227 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
ThisUser@ThisUser-HP-Notebook:~$ alsamixer

```

This bug is really annoying. Anyone knows about this problem and how to fix it?

Best Regards

---

### Post by realjkh on 2020-11-17
Just fixed the bug with command:

"tsched=0"

Don't ask me why, but it fixed the problem for me. I guess there is just one setting with pulseaudio which does not work well with the intel soundcard driver.

Thread closed.

---

### Post by realjkh on 2020-11-18
New information: Unfortunately today the bug is active again, even if i use the command "tsched=0", i even added it to the pulseaudio file. This is very strange to me, so i will leave this thread unsolved.

---

### Post by realjkh on 2020-11-20
After installing WIn 10 updates yesterday und Ubuntu Updates today evening audio works fine again. Closed.

---

