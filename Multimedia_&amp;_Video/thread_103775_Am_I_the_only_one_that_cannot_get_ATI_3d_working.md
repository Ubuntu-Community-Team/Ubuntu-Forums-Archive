---
title: "Am I the only one that cannot get ATI 3d working?"
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by Slovak on 2005-12-14
When I tried to install using steps 1, 2, and 4 on [this]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver") guide, after I reboot all I get is a black screen, and ctrl-alt-f1 does nothing, must do a hard reboot to recovery mode, and other guides I get no errors, just no 3d. Any ideas?
I have an ATI 9800XT on an Asus TUSL2-C mobo with the intel 815 chipset.

---

### Post by Slovak on 2005-12-14
Anyone?
When I follow [this]("http://doc.gwos.org/index.php/Install_ATI_driver") guide posted from darkmatter I can restart the desktop, or reboot, but when I run fglrxinfo, this is the result....
john@ubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Why still Mesa? :confused:

---

### Post by bontux on 2005-12-14
I have pretty much the same problem as you with my ati x800pro. The only way I can get X to start up with a screen is to comment out Load "dri" in xorg.conf.  

I have checked Xorg.0.log in recovery modes for errors and there doesn't seem to be any. I'm still waiting for help with my post to this section.

Your not alone and I don't know how many guides I have tried on this forum all with the same result.

---

### Post by Slovak on 2005-12-15
It is more than just that, it's the fact that no one even offers to try to help fix the problem.

---

### Post by fcser on 2005-12-15
I have an ATI Radeon 9800 pro, 3d does not work for me either :-|

---

### Post by gyrev on 2005-12-16
Same as Bontux, I have to comment "Load DRI" in the module section in order to have X start.

I have a Radeon Xpress 200M (RS480) and the latest (8.20.8 ) drivers from ati, which are supposed to manage this chip.

hope someone find an idea... :???:

---

### Post by jon_z on 2005-12-16
i could not get it working, i was using 64 bit kubuntu and trying to install the 64 bit ati drivers...i downgraded to the 32 bit drivers and no problems installed flawlessly the first time.

---

