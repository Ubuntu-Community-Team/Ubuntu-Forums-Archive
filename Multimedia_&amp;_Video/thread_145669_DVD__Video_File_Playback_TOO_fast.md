---
title: "DVD / Video File Playback TOO fast"
date: 2006-03-16
forum: Multimedia &amp; Video
---

### Post by blackgibson on 2006-03-16
I had hoped to figure this out without bothering you all ( nor did I want a plea for help to be my first post ) but I'm at a loss. The problem is this: DVD and Video ( wma & mpeg tested ) Plays back faster than it should, complete with choppy chipmunk audio. I tried the same DVDs and files in both totem-xine and vlc with the same results. 

Applicable hardware is as follows:

MSI RS482M4-ILD ( ATI Radeon Xpress 200m onboard video)
Azalia HD Audio ( appropriate module hotplug blacklisted )
SB Live! 5.1

Alterations made to a brand new Breezy i386 install:

FGLRX 8.23.7 installed - 2d and 3d working
J2RE 1.5.0_05 installed
Totem-xine to replace Totem-gstreamer via Synaptic
VLC via Synaptic
libdvdcss2-1.2.9-1plf3
w32codecs_20050412-1plf4_i386.deb


Poked around in the options of the aforementioned media players. Couldn't find anything that helped. Any bright ideas?

EDIT: er, forgot to mention that I turned DMA on for the DVD drive

EDIT 2: Applied a workaround for the double speed clock bug and *POOF* no more video playback problems. I feel a bit silly now :/

---

