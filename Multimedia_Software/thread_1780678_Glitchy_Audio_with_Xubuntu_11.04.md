---
title: "Glitchy Audio with Xubuntu 11.04"
date: 2011-06-12
forum: Multimedia Software
---

### Post by metalsubstance on 2011-06-12
Hi all,

I'm having a very strange problem with audio on my laptop (HP dm1z) running Xubuntu 11.04.  I'm not even sure where to begin diagnosing something like this or how to even explain the problem accurately, but I'll do my best.

Basically, I get a very "choppy", "glitchy" audio sound that happens randomly when I try to play any audio at all.  It happens with my laptop's own internal audio (which is currently nonfunctional because of a physically broken audio port) and with any USB audio device that I plug into the laptop.  So I know it's not specifically the audio hardware causing it.  I even replaced the internal storage from an HDD to an SSD, reinstalled Xubuntu 11.04 from scratch, and applied all the latest updates -- and this still didn't do anything to fix the audio.

My hardware: HP dm1z laptop, AMD Fusion E-350 processor, 8 GB RAM, (currently) 120GB OCZ Vertex 2 SSD with the latest firmware applied.

Has anyone else experienced something like this?  Where do I even begin to diagnose such a thing?  I can't run Windows as a host OS on this computer to try a comparison because of lack of storage space.

---

### Post by Toz on 2011-06-12
Two things to try (from terminal window):


1. Delete existing config files:```
rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
Then logout and in again.

If that doesn't work...

2. Edit the /etc/pulse/default.pa file and append **tsched=0** to the line **load-module module-udev-detect** so that it looks like this:```
load-module module-udev-detect tsched=0
```
Then restart pulseaudio:```
pulseaudio -k; sleep 3; pulseaudio -D
```

---

### Post by metalsubstance on 2011-07-01
Making the change to /etc/pulse/default.pa appeared to have solved the problem. Thanks again for your help.

---

### Post by Toz on 2011-07-01
Glad to hear it worked and thanks for reporting back. Can you please mark this thread as solved using the Thread Tools link above? Thanks.

---

