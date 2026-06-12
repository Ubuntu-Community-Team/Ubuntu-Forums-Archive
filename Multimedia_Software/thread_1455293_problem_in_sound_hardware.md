---
title: "problem in sound hardware"
date: 2010-04-15
forum: Multimedia Software
---

### Post by amitasthana on 2010-04-15
I HAVE A COMPAQ SG3530IL DESKTOP and i am running kubuntu (ubuntu installtion inside windows), every time when i start system i got an error that" HDA Intel (ALC662 rev1 Analog) is not working falling playback to playback/recording throuhg the pulse audio sound
other specifications are:-
CPU:	Intel(R) Pentium(R) Dual CPU E2180 @ 2.00GHz
GPU:	Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
Audio:	HDA Intel (ALC662 rev1 Analog)
Audio:	HDA Intel ()

if anybody there please solve this

---

### Post by AcIDx0 on 2010-04-15
1. Try the solution guide at the top of this thread. 
2. Supply more information about the problem. Like dmesg.

---

### Post by Yellow Pasque on 2010-04-15
Go into the KDE system settings and set the pulseaudio device as the preferred one. You could also create an /etc/asound.conf file that routes ALSA apps through pulseaudio:
```
kdesudo kate /etc/asound.conf
```
Copy and paste this into the file:
```
pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default { type pulse }
ctl.!default { type pulse }
```
Save. Quit. Restart.

---

