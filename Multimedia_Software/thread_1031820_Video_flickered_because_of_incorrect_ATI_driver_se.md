---
title: "Video flickered because of incorrect ATI driver setup?"
date: 2009-01-05
forum: Multimedia Software
---

### Post by MrRoberts on 2009-01-05
Good evening all,

My first post here and so far I love the ease of Ubuntu. :)

Firstly, here is my laptop spec...

Alienware
1.8GHz Core Duo
2GB DDR2
120GB SATA 7200RPM
ATI Radeon X1800 256 DDR3

The installation was flawless, picked up my sound card, bluetooth, Intel wireless, etc.

As for the ATI Radeon X1800, I am not sure what is the correct way to enable the full hardware acceleration and 3D functions?

At the moment, when I played a video whether it is from a DVD or the web it would flicker badly.

It is due to incorrect ATI driver setup?

This is what I did...

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

Any suggestions?

---

### Post by 2hot6ft2 on 2009-01-05
The recommended way to install graphics drivers is thru
System>Administration>Hardware Drivers

---

### Post by MrRoberts on 2009-01-05
Do I need to remove the ATI driver setup I made before attempt to use the Hardware Drivers setup?

---

### Post by Melcar on 2009-01-05
By any chance, do you have "3D effects" (Compiz) on?  That will cause video flickering also.

---

### Post by MrRoberts on 2009-01-06
Looks like I am unable to activate the ATI driver via Hardware Drivers manager since it kepts saying that there is a driver in use.

How do I remove the ATI driver I setup and use the Hardware Drivers method?

I have the firework screensaveer on.

It would flicker even when I move my mouse while the screensaver is running. It is annoying.

---

