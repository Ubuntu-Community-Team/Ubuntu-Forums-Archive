---
title: "ATI 9600XT Troubles"
date: 2006-05-18
forum: Multimedia &amp; Video
---

### Post by blip on 2006-05-18
Hi all,

Just made the switch from XP and thus far everything is great.... with one exception... I can't make the blasted ATI drivers work! 

This seems to be a pretty common problem and there are plenty of solutions out there... but the last couple of nights I've been going crazy trying various installations proceedures, fixes, drivers etc. yet I still can't get the card working right.

The problem appears to be here: (from Xorg.0.log):
```
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0d47000 at 0xb7b2f000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

So it looks like the kernel is to blame.  But I've tried every setting of AGPGART (on, off, yes, no) with no avail. (tried just about every other xorg.conf hack that has been suggested here as well.)

It seems like the last resort in ATI driver troubleshooting is to compile a custom kernel.  Being new to this stuff, I'm a bit leary to do so... but I would be willing to try it if I could find a clear, step-by-step tutorial for doing so.

So what should I do next?  Can anyone help me re-do the kernel or is there something else I might have missed?

Thanks in advance and sorry for asking what must be a bit of a tiresome question.

---

### Post by blitzer on 2006-05-19
You can try this link - it worked for me :cool:   I did step by step using Method 2.

[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

---

