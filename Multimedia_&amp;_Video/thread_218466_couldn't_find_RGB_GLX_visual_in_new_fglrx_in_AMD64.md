---
title: "couldn't find RGB GLX visual in new fglrx in AMD64"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by rogeriovinhal on 2006-07-18
I tried the 64 bit forum, but they couldn't help me there.

I have this problem, I have Kubuntu 64bits installed, and want to make fglrx driver work, but after following all the conventional HOWTOs, which by the way worked fine with 32bits, I can't make it work. These codes should explain fair well the problem:

glxinfo
```

roger@Roger:~$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None

```

fglrxinfo
```

roger@Roger:~$ fglrxinfo
Error: couldn't find RGB GLX visual!

```

Xorg.0.log
```

(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x2aaaadd7f000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.26.18
(II) fglrx(0):     Date: Jun 22 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.15-26-amd64-k8
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0x2aaaadd7f000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "UseFBDev" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1600 x 6988
(**) fglrx(0): Video overlay enabled on CRTC1
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
error opening security policy file /etc/X11/xserver/SecurityPolicy

```

I have already tried a lot of things, even the drivers repos and the latest ones, but none seem to get past this message of missing RGB GLX.
This make me think that the problem is not about fglrx, maybe it is with Xorg or Mesa.
I've googled a lot, but no one seem to have a solution to this, it is commonly assigned with wrong Xorg or VGAs drivers installation, not only ATI's.

---

### Post by rogeriovinhal on 2006-07-19
up

---

### Post by theo444 on 2006-07-24
I've been having the same problem! I also have an ATI graphics card (X1600 AMD64 Kubuntu x86_64)...I haven't figured it out either.  I first followed the steps in the "BinaryDriverHowto/ATI" and then other howtos in the 64-bit forums when I was getting the error message "Error: couldn't get an RGB, Double-buffered visual".  However, when I came across your post, I noticed, this segment of /var/log/Xorg.0.log is very similar to yours.

```

[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * [COLOR="Red"]no 3D acceleration available[/COLOR]    
```            *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x0ffe0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)

I'm wondering if there's something wrong with DRI and if that's what at fault.

The reason I point this out is that on my computer the 2D acceleration works fine, but there isn't any 3D acceleration, and it seems the error message *"Error: couldn't get an RGB, Double-buffered visual."* my be a result of this problem.

Correct me if I'm wrong, because I'm just trying to make sense of the error messages in Xorg.0.log.

But, I'll keep looking around for solutions if no one has solved this yet.

---

