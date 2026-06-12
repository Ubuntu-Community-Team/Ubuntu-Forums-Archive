---
title: "How to force resolution (xorg.conf settings)"
date: 2008-08-31
forum: Multimedia Software
---

### Post by Guillaume.l on 2008-08-31
Hi!

Since I've reinstalled Ubuntu (with the current 8.04 version), I can't force the screen resolution (I want 1280*768 and the screen display is still 1024*768). I tried to edit the xorg.conf file but it doesn't seem to influence display configuration, whereas it was possible with previous releases of Ubuntu (and 8.04 updated from 7.10).

I also tried to use the xserver configuration tool (dpkg-reconfigure xserver-xorg), but unlike previous releases it asks for keyboard and mouse settings but nothing about display.

Guillaume.

---

### Post by nbayiha on 2008-08-31
What is the name of your graphic card ? And why do you want to change the resolution ? Can you first give us your system specification?

---

### Post by Guillaume.l on 2008-08-31
My graphic card is an old ATi Rage Pro (*ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)*).

I need to change the resolution because it doesn't fit to my monitor (16:9 monitor).

Do you need any other of my system specifications ?

---

### Post by overdrank on 2008-08-31
HI and have you tried the command ```
gksu displayconfig-gtk
``` and adjust there.

---

### Post by Guillaume.l on 2008-08-31
Thanks overdrank.

I saw a "Large Monitor" checkbox, I checked it, and it allowed me to choose 1280*768 resolution, but display is still a 1024*768 res.

---

