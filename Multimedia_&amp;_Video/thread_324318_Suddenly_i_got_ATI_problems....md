---
title: "Suddenly i got ATI problems..."
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by carsten on 2006-12-23
Hi
I have never had any problems getting the ATI drivers working with my AMD64 system and ATI x700 mobility. I followed my usual guide :[http://ubuntuforums.org/showthread.php?t=204910&highlight=fglrx+howto](http://ubuntuforums.org/showthread.php?t=204910&highlight=fglrx+howto)

The install went without errors and i followed the manual as described. Then after reboot, I test the driver, and instead of the expected output saying ati x700, direct rendering bla bla, I see this:

```

glxincarsten@lappy:~$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 -1  0 r .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None

```

I scanned through the Xorg.log, but found no errors, and it seems the driver is being used.

Xorg.log: [www.cs.aau.dk/~carsten/Xorg.0.log](www.cs.aau.dk/~carsten/Xorg.0.log)
Xorg.conf: [www.cs.aau.dk/~carsten/xorg.conf](www.cs.aau.dk/~carsten/xorg.conf)

Any suggestions??

---

### Post by Stemp on 2006-12-23
From your log :

```
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0x2aaaadfa5000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
```

---

### Post by carsten on 2006-12-23
hmmmm seems that i missed that part....you have any suggestions to fix this?

---

### Post by Stemp on 2006-12-23
are you sure you have the linux-restricted-modules ?

---

### Post by carsten on 2006-12-23
I have /lib64/linux-restricted-modules and /lib/linux-restricted-modules

---

### Post by Stemp on 2006-12-23
Ok, I don't know much about amd64 problems.
But if your kernel is 2.6.17-10-generic (by example) you have to install the linux-restricted-modules-generic package.
But has I already said, I don't know amd64.

---

### Post by carsten on 2006-12-23
that package doesnt exist

---

### Post by Stemp on 2006-12-23
What kernel do you have ?
uname -r

---

### Post by carsten on 2006-12-23
Solved it  - Turned out that i had 2 fglrx.ko in /lib/......
I deleted the one in volatile/, reboot and it works! :)

---

### Post by Stemp on 2006-12-23
Great ;)

---

