---
title: "(EE) fglrx(0): GART is not initialized, disabling DRI"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by zzarr on 2007-01-17
Hello!

The 3d acceleration just don't work on my system!
This time this is the error:

(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Please, I have been trying for weeks, but havn't got the 3d acceleration to work even once. [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

Greetings Zzarr

---

### Post by zzarr on 2007-01-17
I tryed modprobe... but this is what I get...

zzarr@mithril:~$ sudo modprobe fglrx
FATAL: Could not open '/lib/modules/2.6.15-27-686/volatile/fglrx.ko': No such file or directory

And when I checked the log again:

(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

If I copy the /lib/modules/2.6.15-27-686/misc/fglrx.ko to /lib/modules/2.6.15-27-686/volatile/.

modprobe works fine.

But if I reboot my system again, it's gone!

Greetings Zzarr

---

### Post by zzarr on 2007-01-17
I rebooted X, and fore som reason the 3d acceleration works (the first time)

Wonder if I can make it permanent?

Is there anyone who knows why /lib/modules/2.6.15-27-686/volatile/fglrx.ko is removed?
And what script that cause it?

Greetings Zzarr

---

