---
title: "Which driver for Nvidia graphics card?"
date: 2010-06-06
forum: Multimedia Software
---

### Post by T-Keith on 2010-06-06
After having some [trouble]("http://ubuntuforums.org/showthread.php?t=1491708") with Intel graphics I decided to pick up a PCI Nvidia graphics card.  Now I am wondering what driver to use.  Is the open source drive good enough to use or should I install the Nvidia driver?  I know that things are generally easier with the default driver, especially for support on older cards, but I would like to get the best performance I can.  This is for my Dad's computer, so he won't be playing any games, but if it will help with 2D and video that would be great.

The card is an Geforce FX5200 fanless card, I've heard they are well supported in Linux.  The computer is a P4 Dell 3000 with Ubuntu desktop 10.04 32bit. 

thanks,
-Keith

---

### Post by cryptotheslow on 2010-06-06
The NVidia driver will give better 3D and desktop effects support, but the default driver in 10.04 (Nouveau) works very well if you can live without 3D acceleration.

NVidia dropped support for the FX5200 in their latest driver, so you would need version 173.14.25

You should find it available for use in System > Administration > Hardware Drivers

---

### Post by T-Keith on 2010-06-07
Like I said he wont be playing any games, and desktop effects can be kept off.  What about video playback, does either driver support video card acceleration?  That is the main issue.

thanks,
-Keith

---

