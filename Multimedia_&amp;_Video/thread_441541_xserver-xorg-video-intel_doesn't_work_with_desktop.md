---
title: "xserver-xorg-video-intel doesn't work with desktop effects and xv"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by JohnPhys on 2007-05-12
I'm using a gateway laptop with the integrated intel 945 chipset, and I can't get the xserver-xorg-video-intel ("intel") driver to work with xv and desktop effects (x11works, but then mplayer doesn't work as nicely).

Everything worked with the "i810" driver (xserver-xorg-video-i810) and desktop effects enabled.  

I wanted to switch to the xserver-xorg-video-intel driver so I wouldn't have to use 915resolution to get the widescreen resolution support.  Any suggestions?

---

### Post by benanzo on 2007-05-12
I have the same graphics chip as you and I have never had problems using the i810 module for Beryl/AIGLX as well as using 915resolution to get my native resolution 1280x800.

What is your resolution supposed to be?  I wasn't aware that the Intel driver was detecting resolutions any better, I thought it was an Xorg bug.

---

### Post by JohnPhys on 2007-05-12
Well, the i810 driver works just fine, it's with the "intel" driver and the package xserver-xorg-video-intel that I have the issues with xv output when desktop effects are enabled in feisty.  The reason I tried to switch to the xserver-xorg-video-intel driver is because it doesn't need 915 resolution to get my native res (1280x800) to work properly.

---

