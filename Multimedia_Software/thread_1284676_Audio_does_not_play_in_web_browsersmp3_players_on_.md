---
title: "Audio does not play in web browsers/mp3 players on Kubuntu"
date: 2009-10-06
forum: Multimedia Software
---

### Post by jpthompson23 on 2009-10-06
Hey everyone.  I'm running Kubuntu 9.04, and I can't hear anything when streaming flash through firefox or konqueror, nor can I hear anything when playing mp3s on vlc or rhythmbox (i uninstalled amarok).

Just about the only time that I CAN hear audio is when the system is starting up or shutting down (I can still hear the welcome/goodbye piano chimes).

Any idea what would cause this?

sound cards are listed:
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfb8f8000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfb9fc000 irq 34
 2 [HDMI_1         ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfbafc000 irq 37

UPDATE:
When I go to the Multimedia control panel in System Settings, and I test the HDA Intel (ALC1200 Analog) device, I hear the test music.  But I guess that shouldn't really be a surprise since I hear the welcome/goodbye chimes too.

---

### Post by kbm on 2009-10-07
Setting the output channels to use PulseAudio as their first selection (System Settings -> Multimedia) fixed a similar issue for me.

---

### Post by falkTX on 2009-10-07
If the audio sometimes get bad (shuttered?), you can do:
```
killall pulseaudio
```
Then after a few seconds pulseaudio will restart and the audio will be fine again.

---

