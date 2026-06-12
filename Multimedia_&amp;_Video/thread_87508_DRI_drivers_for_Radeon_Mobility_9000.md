---
title: "DRI drivers for Radeon Mobility 9000"
date: 2005-11-08
forum: Multimedia &amp; Video
---

### Post by zachtib on 2005-11-08
i have installed the fglrx drivers and obtained a glxgears score of 1800 on my laptop.  For the first time ever, i had 3d acceleration on an ATI card, and was able to play both America's Army (native) and Counterstrike 1.6 (Cedega) on my laptop.  Then i was told about something called DRI drivers, so i looked them up online, and saw that they required X.org 6.9, but breezy ships with 6.8.  Is there a good howto online for upgrading to 6.9 and then installing the dri drivers? or do i really need X.org 6.9? Can anyonw here help me?

---

### Post by mlomker on 2005-11-08
The ATI drivers provide dri, which is an acronym for *direct rendering infrastructure*.  If you look in your /var/log/Xorg.0.log you'll find some references to dri being loaded.

---

### Post by zachtib on 2005-11-08
im talking about the ones online at dri.freedesktop.org, apparently they arent made by ati, and provide better support for older radeon cards

---

### Post by mlomker on 2005-11-08
[QUOTE=zachtib]im talking about the ones online at dri.freedesktop.org, apparently they arent made by ati, and provide better support for older radeon cards[/QUOTE]

Ok.  I'm not sure if the ATI & Radeon drivers that come with Breezy are from that project or not.  I haven't seen very good performance from any driver that uses MESA, though.

---

