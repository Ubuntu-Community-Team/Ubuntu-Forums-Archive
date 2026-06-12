---
title: "No more 3D acceleration after Natty"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hambone79 on 2011-04-18
I have a laptop that I use specifically for testing new software and new versions of Ubuntu. A week ago I had it up and running without issues under 10.10 with full desktop effects and the Docky dock. Even though the laptop has an older Radeon Xpress 200m video card, it always ran pretty smooth.

Over the weekend I decided to go ahead and upgrade to the latest Natty beta, but now my 3D acceleration is completely broken. I had read on the forums that there are issues with the open source ATI driver in Natty and that the best option would be to install an updated driver from xorg-edgers ppa. Unfortunately this did no fix the problem so I am stuck running everything in 2D software rendered mode.

I should also point out that every attempt that I have made to manually start compiz, glxgears, or glxinfo immediately results in a segfault.

Anyone have an idea what is going on and how to fix it? I would really like to give Unity a test drive in 3D.

---

### Post by hambone79 on 2011-04-20
Anybody? I'm still unable to get 3D working...everything segfaults.

---

### Post by xgt001 on 2011-04-21
open source ati drivers work fine for me in natty but it has poor power management
did u try installing proprietary drivers?

---

### Post by dino99 on 2011-04-21
maybe your hardware cant run both compiz+unity. So test by removing, into synaptic:

- ubuntu-desktop
- unity

---

### Post by clhsharky on 2011-04-22
hambone79


Did you upgrade or fresh install? And did you have xorg-edgers if you upgraded?
> *IMPORTANT NOTICE* - If you are upgrading from one release to another and are using this PPA, be sure to install ppa-purge and use it to downgrade all of this PPA's packages before the upgrade or you will have a broken system.
[https://launchpadlibrarian.net/27204082/xorg-edgers-64.png](https://launchpadlibrarian.net/27204082/xorg-edgers-64.png)

I use OSS R300g radeon driver (default) in Natty for our chips and it works nicely.


Sharky

---

### Post by hambone79 on 2011-04-22
Ok, here is what I have tried so far:

1. Upgraded from 10.10 (working perfectly) to 11.04 beta. When I did this everything relying on 3D acceleration is now disabled: boot splash, Unity, Ubuntu Classic, Docky..nothing works.
2. Someone on the forums had mentioned to try the xorg-edgers ppa because it has more up to date drivers. I gave it a try and everything installed smoothly but once again, no 3D acceleration and everything was stuck in 2D.
3. Ran the ppa-purge utility and reverted back to the xorg that came with Natty. Still stuck in 2D.

I should also point out a few other points:

1. In all cases I'm using the open source ati driver because the Radeon Xpress 200m is not supported by the binary driver.
2. When I launch glxgears or glixnfo it immediately segfaults. This leads me to believe it may be a bug.

---

### Post by hambone79 on 2011-04-23
Ok, this has me completely stumped...

Here is the Xorg log:

```

[   114.030] (II) RADEON(0): EDID vendor "LPL", prod id 0
[   114.030] (II) RADEON(0):     EDID quirk: Detailed timings give vertical size in cm.
[   114.030] (II) RADEON(0): Printing DDC gathered Modelines:
[   114.030] (II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
[   114.030] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[   114.030] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[   114.030] (II) RADEON(0): Manufacturer: LPL  Model: 0  Serial#: 0
[   114.030] (II) RADEON(0): Year: 2005  Week: 0
[   114.030] (II) RADEON(0): EDID Version: 1.2
[   114.030] (II) RADEON(0): Digital Display Input
[   114.030] (II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[   114.030] (II) RADEON(0): Gamma: 2.20
[   114.030] (II) RADEON(0): No DPMS capabilities specified
[   114.030] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   114.030] (II) RADEON(0): First detailed timing is preferred mode
[   114.030] (II) RADEON(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
[   114.030] (II) RADEON(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
[   114.030] (II) RADEON(0): Manufacturer's mask: 0
[   114.030] (II) RADEON(0): Supported detailed timing:
[   114.030] (II) RADEON(0): clock: 71.2 MHz   Image Size:  289 x 210000 mm
[   114.030] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[   114.030] (II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
[   114.030] (II) RADEON(0):  LGPhilipsLCD
[   114.030] (II) RADEON(0):  LP154W01-TLA2
[   114.030] (II) RADEON(0): EDID (in hex):
[   114.030] (II) RADEON(0): 	00ffffffffffff00320c000000000000
[   114.030] (II) RADEON(0): 	000f0102802115780a0f109758528828
[   114.030] (II) RADEON(0): 	23505400000001010101010101010101
[   114.030] (II) RADEON(0): 	010101010101d51b00a0502017303020
[   114.030] (II) RADEON(0): 	26002115100000190000000000000000
[   114.030] (II) RADEON(0): 	00000000000000000000000000fe004c
[   114.031] (II) RADEON(0): 	475068696c6970734c43440a000000fe
[   114.031] (II) RADEON(0): 	004c503135345730312d544c41320008
[   114.031] (II) RADEON(0): EDID vendor "LPL", prod id 0
[   114.031] (II) RADEON(0):     EDID quirk: Detailed timings give vertical size in cm.
[   114.031] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0

```

And here is the output from dmesg:

```

[   34.533517] [drm] Initialized drm 1.1.0 20060810
[   34.754278] [drm] radeon defaulting to kernel modesetting.
[   34.754285] [drm] radeon kernel modesetting enabled.
[   34.754388] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[   34.766694] [drm] initializing kernel modesetting (RS400 0x1002:0x5A62).
[   34.766745] [drm] register mmio base: 0xC0000000
[   34.766748] [drm] register mmio size: 65536
[   34.766914] [drm] Generation 2 PCI interface, using max accessible memory
[   34.766957] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   34.766960] [drm] Driver supports precise vblank timestamp query.
[   34.767000] [drm] radeon: irq initialized.
[   34.767311] [drm] Detected VRAM RAM=128M, BAR=256M
[   34.767318] [drm] RAM width 128bits DDR
[   34.768967] [drm] radeon: 128M of VRAM memory ready
[   34.768970] [drm] radeon: 512M of GTT memory ready.
[   34.768999] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   34.796000] [drm] radeon: 2 quad pipes, 1 z pipes initialized.
[   34.808788] [drm] Loading R300 Microcode
[   34.944282] [drm] radeon: ring at 0x0000000060001000
[   34.944311] [drm] ring test succeeded in 2 usecs
[   34.944556] [drm] radeon: ib pool ready.
[   34.944650] [drm] ib test succeeded in 0 usecs
[   34.945086] [drm] Panel ID String: LPL                     
[   34.945090] [drm] Panel Size 1280x800
[   34.945208] [drm] Radeon Display Connectors
[   34.945211] [drm] Connector 0:
[   34.945213] [drm]   VGA
[   34.945217] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   34.945219] [drm]   Encoders:
[   34.945221] [drm]     CRT1: INTERNAL_DAC2
[   34.945224] [drm] Connector 1:
[   34.945226] [drm]   LVDS
[   34.945229] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   34.945231] [drm]   Encoders:
[   34.945234] [drm]     LCD1: INTERNAL_LVDS
[   34.945236] [drm] Connector 2:
[   34.945238] [drm]   S-video
[   34.945240] [drm]   Encoders:
[   34.945242] [drm]     TV1: INTERNAL_DAC2
[   35.143331] [drm] fb mappable at 0xD0040000
[   35.143336] [drm] vram apper at 0xD0000000
[   35.143338] [drm] size 4096000
[   35.143341] [drm] fb depth is 24
[   35.143343] [drm]    pitch is 5120
[   35.148173] fb0: radeondrmfb frame buffer device
[   35.148176] drm: registered panic notifier
[   35.148190] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0

```

I have no idea what is causing my problem because I don't see any errors popping up, but I still get a segfault every single time I try to start anything using 3D.

---

### Post by hambone79 on 2011-04-25
Ok...got some new information:

```

        ldd /usr/bin/glxinfo
	linux-gate.so.1 =>  (0xb78e2000)
	[COLOR="Red"]libGL.so.1 => /usr/lib/fglrx/libGL.so.1 (0xb77db000)[/COLOR]
	libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xb76c0000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb755e000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xb7545000)
	libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xb7536000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb7510000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb74f4000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb74ef000)
	libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xb74d6000)
	/lib/ld-linux.so.2 (0xb78e3000)
	libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xb74d2000)
	libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xb74cc000)
```

It appears that my machine is trying to load the libGL.so.1 from fglrx rather than the one from mesa. My only problem is I don't know how to force it to use the mesa version. Anyone have an idea how to fix this?

---

### Post by lavinog on 2011-04-25
Have you tried a fresh install?

---

### Post by hambone79 on 2011-04-25
I just did an "apt-get remove fglrx" and now everything works perfectly!

---

