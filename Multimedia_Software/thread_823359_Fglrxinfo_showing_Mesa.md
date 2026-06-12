---
title: "Fglrxinfo showing Mesa"
date: 2008-06-09
forum: Multimedia Software
---

### Post by primky on 2008-06-09
I installed Ati drivers, but when i do "fglrxinfo", it says Mesa, not ATI.

Please don't reffer me to "How to remove Mesa drivers", as i already done that:

> Remove the package xserver-xgl.


This is something interesting:
> primky@deskto-0x:~$ **less /var/log/Xorg.0.log |grep EE**
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
**(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.** 


---

### Post by sim-value on 2008-06-09
You are in the same boat like me i never even had that installed my log:
```
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.90
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0xe0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,768) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7423
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 14
(**) fglrx(0): Option "XaaNoOffscreenPixmaps" "1"
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
Fail to query CF Candidates
(==) RandR enabled
...
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
```
Thats weird i definitly do have the Kernel module installed (i think ...)
ATI drivers are the worst thing i met in relation to linux ...
BTW which graphics car you have ?

---

### Post by primky on 2008-06-10
I have ATI Radeon X1650 Pro.

Someone with this card PLEASE tell us how you made it work. More than 100 users would be grateful, i'm sure!

---

