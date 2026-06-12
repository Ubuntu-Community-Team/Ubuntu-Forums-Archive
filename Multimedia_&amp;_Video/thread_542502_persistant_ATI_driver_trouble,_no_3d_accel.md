---
title: "persistant ATI driver trouble, no 3d accel"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by Alarictric on 2007-09-04
so i've tried every method i could find to install my ATI drivers on 7.04 but still cannot get 3d support.  Im still learning the whole terminal thing, as im a recent windows convert. so i may need to be walked through this.  i was looking at my xorg.0.log file and found this section here...

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.34.8
(II) fglrx(0):     Date: Feb 20 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x4000 at 0xb7ca0000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


is this information useful in helping me fix my situation? and if so, can anybody tell me what to do?  if you need more information from me such as other log files or config info, just ask and i can post more info.

vid card is a ati x800xt, agp

---

