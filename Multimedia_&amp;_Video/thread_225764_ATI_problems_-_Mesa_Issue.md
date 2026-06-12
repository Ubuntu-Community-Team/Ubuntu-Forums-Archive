---
title: "ATI problems - Mesa Issue"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by core on 2006-07-30
Hi all. I had i few problems some time ago installing the ATI drivers for my laptop graphics card, but now I went deeper into it and was able to install them successfully. Now my problem is get them to work properly.

I've installed them in different ways. The last time I did it like this:

-apt-get update
-remove xorg-driver-fglrx and linux-restricted-modules for my kernel
-getting my xorg.conf back to 'ati' driver, if needed
-reboot.

-reinstalled linux-restricted-modules for my kernel, and then the xorg-driver-fglrx
-xorg.conf with "fglrx" again, instead of "ati"
-reboot.

-ran 'fglrxinfo' command, which returned this:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

So I guess I'm another victim of the Mesa Issue. "strace fglrxinfo 2>&1 | less" returns a bunch of text i find unconclusive. "sudo dmesg | grep fgrlx" returns nothing. Sym links on /usr/lib/ for libGL are correct. /usr/lib/dri wasn't linked to /usr/lib/xorg/modules/dri, but i linked it and the same happened.
Only conclusive output I found was when i grepped /var/log/Xorg.0.log. Some lines are:

(WW) fglrx(0): DRI is not supported on Radeon 9000/9100 IGP (RS300/RS350) hardware.
(==) fglrx(0): OpenGL ClientDriverName: "on_igp9x00_we_do_not_support_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe0501000 (size=0x07aff000)
(II) fglrx(0): UMM area:     0x38501000 (size=0x07aff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) fglrx(0): doing DRIScreenInit
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0x38000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled

So, my graphics card is not supported by these ATI drivers? Where can I get the last compatible version of the drivers? Thanks in advance for any support or ideas.

---

### Post by core on 2006-07-31
up :( anyone?

---

### Post by rippon on 2006-08-01
What is the Mesa Issue?

---

### Post by TobbeR on 2006-08-01
Hi
I had the same problems and tried everything from this forum, nothing helped. Then I stumbled on this site
[http://www.darkwizzard.rulz.hu/](http://www.darkwizzard.rulz.hu/) under Articles

Trust me, he knows what he's talking about, I fixed my problems in 10 minutes.

T

---

