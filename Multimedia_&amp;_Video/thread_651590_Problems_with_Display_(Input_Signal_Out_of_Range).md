---
title: "Problems with Display (Input Signal Out of Range)"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by tarlejh on 2007-12-27
Help, on my new Ubuntu PC, everything boots OK, and I had it working earlier, but suddenly I rebooted and my display is basically unreadable.

The monitor, an HPvs15 says "Monitor Signal Out of Range, Change Settings to 1024 x 768" or something, but how do I do this if I can't see what I'm doing?  I can run commands in Terminal but it's hard to see what I'm typing.

I have an ATI Radeon Video Card.

---

### Post by godfree2 on 2007-12-27
on bootup hit ESC
to get to the grub menu
hit 'e' to edit the boot up line
on the kernel line add this
xrefrsh=70
or
xrefresh=70
(someone correct me if I am wrong here)
then enter to boot

the added command will reduce the screen refresh rate, if the rate is too high the screen will be quite darker. The monitor I am on now, is best set to 75hz even though ubuntu puts it into 85hz (too high) on bootup. After bootup adjust the display settings to a lower refresh rate

if you can't even get the graphics screen up,
boot up and edit the grub line again, this time put in 
xdrvr=vesa
this will give you a temporary lower resolution until you can diagnose the problem

---

