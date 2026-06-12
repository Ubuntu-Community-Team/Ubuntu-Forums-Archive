---
title: "Please help - ATI X1950XTX + Feisty"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by kreyszig on 2007-03-01
Hi All, 

I'd really appreciate some help getting my X1950XTX to run on feisty.
I have tried all methods at 
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
and [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) to no avail. 
According to the first link above, feisty isn't supporting ATI's own drivers yet, which is a shame, but i digress..
here is my fglrxinfo 

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

an interesting part of my  /var/log/Xorg.0.log:

(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb6a11000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.33.6
(II) fglrx(0):     Date: Jan  8 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
**(WW) fglrx(0): Kernel Module version does *not* match driver.**
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb6a11000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


I'm guessing I have to recompile my kernel module amongst other things - how do I go about doing that? 
Your help very much appreciated!

---

### Post by igknighted on 2007-03-01
> **kreyszig said:**
> Hi All, 

I'd really appreciate some help getting my X1950XTX to run on feisty.
I have tried all methods at 
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
and [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) to no avail. 
According to the first link above, feisty isn't supporting ATI's own drivers yet, which is a shame, but i digress..
here is my fglrxinfo 

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

an interesting part of my  /var/log/Xorg.0.log:

(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb6a11000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.33.6
(II) fglrx(0):     Date: Jan  8 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
**(WW) fglrx(0): Kernel Module version does *not* match driver.**
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb6a11000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


I'm guessing I have to recompile my kernel module amongst other things - how do I go about doing that? 
Your help very much appreciated!

The fglrx drivers you are trying to use ARE the ati drivers that are incompatible with fiesty.  The problem is with ATI drivers not being able to compile the kernel module for the 2.6.20-* kernel.  If you browse the fiesty forum on this site there is a patch for the ATI driver, or you can manually install a 2.6.19 kernel in the meantime and then build the module for that kernel.

---

### Post by Mateo on 2007-03-11
i have the same problem, how do you fix it.

---

