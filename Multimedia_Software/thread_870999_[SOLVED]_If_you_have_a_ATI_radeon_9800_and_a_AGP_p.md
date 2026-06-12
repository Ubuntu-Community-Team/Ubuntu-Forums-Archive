---
title: "[SOLVED] If you have a ATI radeon 9800 and a AGP port, I need your help."
date: 2008-07-26
forum: Multimedia Software
---

### Post by DOS4dinner on 2008-07-26
If you have a ATI Radeon 9800 running full power in Ubuntu, could you tell me how you did so? A couple of weeks ago a made the "how do you remove mesa drivers" thread. After much trying and pain, my card still cannot do 3D.I have tried most basic things, like envy, messing with my xorg.conf a bit, using the opensource driver, etc. but none appear to work. Currently, I am using the open source driver.

Also, does Ubuntu have problems with AGP graphic card ports? That is what my computer uses and I thought it might be the problem (maybe not, just a guess).

Here is my xorg.conf (some lines were left over from previous attempts at fixing it)
```


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	Option		"DRI"	"1"
	Option		"UseInternalAGPGART"	"0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"vbe"
	Load		"ddc"
	Load		"freetype"
	Load		"int10"
	Load		"glx"
	Load		"dri"
	Load		"extmod"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
EndSection
```

and the log (the important part where the only (ee) is):

```
II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xf0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(WW) RADEON(0): [agp] AGP not available
(EE) RADEON(0): [agp] AGP failed to initialize. Disabling the DRI.
(II) RADEON(0): [agp] You may want to make sure the agpgart kernel module
is loaded before the radeon kernel module.
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf8bba000 at 0xb7f69000
(II) RADEON(0): [drm] Closed DRM master.
```

Thanks in advance.

---

### Post by DOS4dinner on 2008-07-29
Bumped! in the name of LOVE............Before you break my heart.......
Someone here must use this card, Right?
(if bumping is illegal on this forum, let me know and forgive me for my error)
Nevermind. Found the bug. Just had to blacklists some intel problem files.

---

### Post by dustorm on 2008-08-25
I've been using the latest drivers from ATI and the standard install script actually works for the last two releases.  They've been releasing new drivers once a month for nearly a year now.

I've been downloading the driver from ati, then using the command line to start it (cd to the directory where the file is then 'sudo ./ati-driver-installer-8-8-x86.x86_64.run') then just use the graphical installer to install.

---

