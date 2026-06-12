---
title: "Bad configuration or bug on Intel i810 video driver?"
date: 2008-09-27
forum: Multimedia Software
---

### Post by Vladimir Hidalgo on 2008-09-27
I got this every time I start up the system:

```
[  227.298100] [drm] Initialized i810 1.4.0 20030605 on minor 0
[  227.299782] mtrr: base(0x44000000) is not aligned on a size(0x180000) boundary
[  227.314718] [drm] Using v1.4 init.
[  230.613924] [drm:drm_release] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[  230.613938] 	driver to use reclaim_buffers_idlelocked() instead.
[  230.613942] 	I will go on reclaiming the buffers anyway.
```

I'm using Ubuntu 8.04, updated to this day. 

I have this in xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 810"
	Busid		"PCI:0:1:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
	Option "DRI" "true"
	#Option "BackingStore" "true"
	Option "RenderAccel" "true" # render accel is enabled by default
	Option "AllowGLXWithComposite" "true"
EndSection
```

xcompmgr works well, and I don't notice any glitch on the video, but I wanted to report it anyway.

Let me know if it can be a bug, so it can be reported on a more appropriate

```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
 site.
```

---

### Post by wolfen69 on 2008-09-27
i'm not assuming you are a newbie, but if you are, one way to see if it might be a hardware problem is to reinstall with a checksummed iso. if the problem is still there, it would be a strong indication that some hardware is broken.

with intel chipsets, there really shouldn't be a problem. (except for the occasional sound tweak)

perhaps someone else can shed some light on this.

---

### Post by Vladimir Hidalgo on 2008-09-28
I don't think it's that, because I had installed with an original CD, shipped from shipit.ubuntu.com

Also there had been recent upgrades to this driver, but this problem has been there forever. For example there is this similar thread: [http://ubuntuforums.org/showthread.php?t=272344](http://ubuntuforums.org/showthread.php?t=272344)

---

