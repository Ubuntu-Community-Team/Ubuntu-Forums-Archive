---
title: "Interesting Item In Today's Testing"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by PGHammer on 2010-09-22
I just installed the latest (as in compiled today) kernel from the Kernel Mainline PPA (newer than the kernel from Maverick-daily, actually), alongside the latest code from xorg-edgers PPA.  2D seriously sped up (over edgers + base kernel, let alone over base Maverick daily); however, I also found out why DRI is a non-starter (at least at this point).  While the latest kernel *does* have KMS enabled by default (and it works, to an extent, with HD5xxx), the support for color tiling in KMS (at least for HD5xxx) isn't there - as far as I can see, that is the only item throwing a wrench into support for DRI2 (or anything else) for Evergreen as it stands.

Here's the Xorg.0.log (relevant section only):

```


	Information		ATI Radeon HD 5450, CEDAR
	Information	[    15.865] (II) VESA: driver for VESA chipsets: vesa
	Information	[    15.865] (II) FBDEV: driver for framebuffer: fbdev
	Information	[    15.865] (++) using VT number 7
	Information	
	Information	[    15.866] (II) [KMS] Kernel modesetting enabled.
	Information	[    15.866] (WW) Falling back to old probe method for vesa
	Information	[    15.866] (WW) Falling back to old probe method for fbdev
	Information	[    15.866] (II) Loading sub module "fbdevhw"
	Information	[    15.866] (II) LoadModule: "fbdevhw"
	Information	[    15.866] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
	Information	[    15.866] (II) Module fbdevhw: vendor="X.Org Foundation"
	Information	[    15.866] 	compiled for 1.9.0, module version = 0.0.2
	Information	[    15.866] 	ABI class: X.Org Video Driver, version 8.0
	Information	[    15.866] (II) RADEON(0): Creating default Display subsection in Screen section
	Information		"Default Screen Section" for depth/fbbpp 24/32
	Information	[    15.866] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
	Information	[    15.866] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
	Information	[    15.866] (==) RADEON(0): Default visual is TrueColor
	Information	[    15.867] (==) RADEON(0): RGB weight 888
	Information	[    15.867] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
	Information	[    15.867] (--) RADEON(0): Chipset: "ATI Radeon HD 5450" (ChipID = 0x68f9)
	Information	[    15.867] (II) RADEON(0): PCIE card detected
	Information	[    15.867] drmOpenDevice: node name is /dev/dri/card0
	Information	[    15.867] drmOpenDevice: open result is 8, (OK)
	Information	[    15.867] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
	Information	[    15.867] drmOpenDevice: node name is /dev/dri/card0
	Information	[    15.867] drmOpenDevice: open result is 8, (OK)
	Information	[    15.867] drmOpenByBusid: drmOpenMinor returns 8
	Information	[    15.867] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
	Information	[    15.867] (II) RADEON(0): KMS Color Tiling: disabled
	Information	[    15.872] (II) RADEON(0): Output HDMI-0 has no monitor section
	Information	[    15.955] (II) RADEON(0): Output DVI-0 has no monitor section
	Information	[    15.970] (II) RADEON(0): Output VGA-0 has no monitor section
	Information	[    15.974] (II) RADEON(0): EDID for output HDMI-0
	Information	[    16.032] (II) RADEON(0): EDID for output DVI-0
	Information	[    16.033] (II) RADEON(0): Manufacturer: ACR  Model: a0  Serial#: 2434802049
	Information	[    16.033] (II) RADEON(0): Year: 2009  Week: 12
	Information	[    16.033] (II) RADEON(0): EDID Version: 1.3
	Information	[    16.033] (II) RADEON(0): Digital Display Input
	Information	[    16.033] (II) RADEON(0): Max Image Size [cm]: horiz.: 51  vert.: 29
	Information	[    16.033] (II) RADEON(0): Gamma: 2.20
	Information	[    16.033] (II) RADEON(0): DPMS capabilities: Off
	Information	[    16.033] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
	Information	[    16.033] (II) RADEON(0): First detailed timing is preferred mode
	Information	[    16.033] (II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
	Information	[    16.033] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
	Information	[    16.033] (II) RADEON(0): Supported established timings:
	Information	[    16.033] (II) RADEON(0): 720x400@70Hz
	Information	[    16.033] (II) RADEON(0): 640x480@60Hz
	Information	[    16.033] (II) RADEON(0): 640x480@67Hz
	Information	[    16.033] (II) RADEON(0): 800x600@56Hz
	Information	[    16.033] (II) RADEON(0): 800x600@60Hz
	Information	[    16.033] (II) RADEON(0): 1024x768@60Hz
	Information	[    16.033] (II) RADEON(0): 1024x768@70Hz
	Information	[    16.033] (II) RADEON(0): Manufacturer's mask: 0
	Information	[    16.033] (II) RADEON(0): Supported standard timings:
	Information	[    16.033] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
	Information	[    16.033] (II) RADEON(0): #1: hsize: 1280  vsize 800  refresh: 60  vid: 129
	Information	[    16.033] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
	Information	[    16.033] (II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
	Information	[    16.033] (II) RADEON(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
	Information	[    16.033] (II) RADEON(0): #5: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
	Information	[    16.033] (II) RADEON(0): Supported detailed timing:
	Information	[    16.033] (II) RADEON(0): clock: 148.5 MHz   Image Size:  510 x 287 mm
	Information	[    16.033] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
	Information	[    16.033] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
	Information	[    16.033] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
	Information	[    16.033] (II) RADEON(0): Monitor name: Acer H233H
	Information	[    16.033] (II) RADEON(0): Serial No: LFS0W0104300
	Information	[    16.033] (II) RADEON(0): EDID (in hex):
	Information	[    16.033] (II) RADEON(0): 	00ffffffffffff000472a00081212091
	Information	[    16.033] (II) RADEON(0): 	0c13010380331d782aee95a3544c9926
	Information	[    16.033] (II) RADEON(0): 	0f5054b30c00714f810081809500b300
	Information	[    16.033] (II) RADEON(0): 	d1c001010101023a801871382d40582c
	Information	[    16.033] (II) RADEON(0): 	4500fe1f1100001e000000fd00384b1e
	Information	[    16.033] (II) RADEON(0): 	5311000a202020202020000000fc0041
	Information	[    16.033] (II) RADEON(0): 	6365722048323333480a2020000000ff
	Information	[    16.033] (II) RADEON(0): 	004c46533057303130343330300a0051
	Information	[    16.034] (II) RADEON(0): Printing probed modes for output DVI-0
	Information	[    16.034] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
	Information	[    16.034] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
	Information	[    16.050] (II) RADEON(0): EDID for output VGA-0
	Information	[    16.050] (II) RADEON(0): Output HDMI-0 disconnected
	Information	[    16.050] (II) RADEON(0): Output DVI-0 connected
	Information	[    16.050] (II) RADEON(0): Output VGA-0 disconnected
	Information	[    16.050] (II) RADEON(0): Using exact sizes for initial modes
	Information	[    16.050] (II) RADEON(0): Output DVI-0 using initial mode 1920x1080
	Information	[    16.050] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
	Information	[    16.050] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:1f7d7000
	Information	[    16.050] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
	Information	[    16.050] (==) RADEON(0): DPI set to (96, 96)
	Information	[    16.050] (II) Loading sub module "fb"
	Information	[    16.050] (II) LoadModule: "fb"
	Information	[    16.051] (II) Loading /usr/lib/xorg/modules/libfb.so
	Information	[    16.051] (II) Module fb: vendor="X.Org Foundation"
	Information	[    16.051] 	compiled for 1.9.0, module version = 1.0.0
	Information	[    16.051] 	ABI class: X.Org ANSI C Emulation, version 0.4
	Information	[    16.051] (II) Loading sub module "ramdac"
	Information	[    16.051] (II) LoadModule: "ramdac"
	Information	[    16.051] (II) Module "ramdac" already built-in
	Information	[    16.051] (II) RADEON(0): GPU accel disabled or not working, using shadowfb for KMS
	Information	[    16.051] (II) Loading sub module "shadow"
	Information	[    16.051] (II) LoadModule: "shadow"
	Information	[    16.051] (II) Loading /usr/lib/xorg/modules/libshadow.so
	Information	[    16.051] (II) Module shadow: vendor="X.Org Foundation"
	Information	[    16.051] 	compiled for 1.9.0, module version = 1.1.0
	Information	[    16.051] 	ABI class: X.Org ANSI C Emulation, version 0.4
	Information	[    16.051] (II) UnloadModule: "vesa"
	Information	[    16.052] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
	Information	[    16.052] (II) UnloadModule: "fbdev"
	Information	[    16.052] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
	Information	[    16.052] (II) UnloadModule: "fbdevhw"
	Information	[    16.052] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
	Information	[    16.052] (--) Depth 24 pixmap format is 32 bpp
	Information	[    16.052] (II) RADEON(0): Front buffer size: 8704K
	Information	[    16.052] (II) RADEON(0): VRAM usage limit set to 456505K
	Information	[    16.052] (==) RADEON(0): Backing store disabled
	Information	[    16.052] (WW) RADEON(0): Direct rendering disabled
	Information	[    16.052] (II) RADEON(0): Acceleration disabled 
```

As you can see, both radeon-drm and KMS are *active* (as they should be); however, KMS color-tiling support is turned off, which seems to throw a wrench into both direct-rendering and hardware acceleration.  Is this indeed true, or is there something else that needs doing?

---

### Post by BwackNinja on 2010-09-22
For 3D acceleration, you need to install the evergreen_accel branch of xf86-video-ati ([http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/log/?h=evergreen_accel](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/log/?h=evergreen_accel)) and some drm stuff will only be coming to the 2.6.37 kernel. You would have to install drm-radeon-testing ([http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing](http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=shortlog;h=refs/heads/drm-radeon-testing)) to get that stuff now.

---

