---
title: "Geforce2 MX/MX 400 problems. Can't get past black screen"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by sansrage on 2007-05-02
Hey guys, noob trying to figure this out.....

I've changed my device settings to 

Section "Device"
Identifier "6600"
Driver "nvidia"
BusId "PCI:0x0110

and Fiesty loaded up smaller fonts and a better resolution, but when it tried loading the desktop it failed out and said No screen loaded....I know the problem is it's going to a default onboard Intel chipset instead of my GeForce2 card, but I'm confused how it's to read 

(currently, it's)
Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller]
Moniter "HP w1907"
Default Depth 24
Subsection "Display"
(and then all the values)

What do I plug in for the GeForce2 MX/MX 400 card? I've read the readme.txt and I'm still confused....I'm sooo close!!!

---

### Post by atlfalcons866 on 2007-05-02
1st of all i dont know what to do but it would help others what ubuntu version you are using

---

### Post by sansrage on 2007-05-02
awwww, crap...guess it would!! I'm running Ubuntu Fiesty.

---

