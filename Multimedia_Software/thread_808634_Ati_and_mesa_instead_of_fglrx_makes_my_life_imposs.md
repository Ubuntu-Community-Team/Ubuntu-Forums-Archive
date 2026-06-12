---
title: "Ati and mesa instead of fglrx makes my life impossible"
date: 2008-05-26
forum: Multimedia Software
---

### Post by mizar001 on 2008-05-26
Hi. I have Feisty and an ATI radeon 9550 . With it i lived well for some time , until i decided to do an update yesterday.

My fglrx drivers (installed with 'restricted driver manager') are no more  working. flgrxInfo returns :

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

and 
$>tail -n10000 /var/log/Xorg.0.log |grep fglrx
gives me :
...
(II) Loading sub module "fglrxdrm"
...
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work


The xorg file seems fine (it shows driver='fglrx'). 


I tried 'ati proprietary drivers' but they are not good (put some bad lines on my screen), i tried also the 'modules.dep way' as seen in some threads, but nothing is getting me in the right direction. How to solve the mismatch version kernel problem ?

---

### Post by Gunman1982 on 2008-05-26
Revert to the linux kernel you used before, if you reboot you probably have 4 options or?

Ubuntu version blah-17
Ubuntu version blah-17 (safemode)
Ubuntu version blah-16             <-- choose this one
Ubuntu version blah-16 (safemode

---

### Post by |{urse on 2008-05-26
I had this very same problem with my x1650. The only thing that fixed it was an upgrade to hardy for some reason.

[http://ubuntuforums.org/showthread.php?t=780455](http://ubuntuforums.org/showthread.php?t=780455) 

You can try following this howto

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

a lot of users report success with it.

---

