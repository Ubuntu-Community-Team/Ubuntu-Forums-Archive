---
title: "Video playback problems"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by likwid on 2007-03-22
Hi

When trying to play avi files i get a green screen in both movie player and vlc. I have the nvidia drivers installed and all codecs. I admit i'm pretty new to this and only having the problems with this new install due to the fact that automatix is down. Any help would be very much appreciated as i'm installing a media pc and have a captive and (at least  at this point) very patient audience who don't understand why i'm not installing windows...

---

### Post by Big_Croc7 on 2007-03-23
VLC dosen't work correctly with all codecs - have you tried gxine? (search for gxine in synaptic).  Might be worth a shot - it's the only one that plays DVDs correctly on my system, for example, at least at the moment.

---

### Post by likwid on 2007-03-26
Hi

Sorry for not answering sooner. I managed to get vlc working by changing video output module from default output to X11. How would i go about changing such settings in totem? It doesn't seem to be an option in the gui.

Any more help would be very appreciated.

---

### Post by Big_Croc7 on 2007-03-27
hmm don't know... I'm afraid I can't help much more... are you using xv output by defaut? (i.e. have you tried installing compiz/beryl?) If so this might be the source of the problem; maybe if you post your graphics card and xorg file (gedit /etc/X11/xorg.conf and copy the contents) someone else will be able to help.
Good luck :-)

---

