---
title: "Strange ATI problem"
date: 2005-11-03
forum: Multimedia &amp; Video
---

### Post by hed on 2005-11-03
I've installed the latest ATI propietary driver, but I can't get Direct Rendering to work.
The strange think is that I've a bit of 3D acceleration, but not full.
If I type "lsmod | grep fglrx" the result is:
fglrx                 260704  7
agpgart                34792  2 intel_agp,fglrx

I think the problem is that the driver uses the internal AGP, but I don't know how to not use it.
I've tried writing "Option "UseInternalAGPART"      "no"" in xorg.conf, but it don't works. Also tried with the configuration tool but don't works...

Any ideas?

THX!

P.S: My card is an ATI Mobility Radeon 9600 PRO

---

### Post by mlomker on 2005-11-04
You didn't provide a lot of information.  General troubleshooting:

```

fglrxinfo
dmesg | grep fgrlx

```

Also look through /var/log/Xorg.0.log for errors.

---

### Post by hed on 2005-11-06
fglrxinfo says:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

And dmesg | grep fglrx  don't say nothing :S

Here is a part of my Xorg.0.log, maybe here is the problem but don't know:

> (II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9200 SE (RV280 5964),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9550 (M12 4E56), RADEON 9500 (R300 4144),
	RADEON 9600 TX (R300 4146), FireGL Z1 (R300 4147),
	RADEON 9700 PRO (R300 4E44), RADEON 9500 PRO/9700 (R300 4E45),
	RADEON 9600 TX (R300 4E46), FireGL X1 (R300 4E47),
	RADEON 9800 SE (R350 4148), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9800 PRO (R350 4E48),
	RADEON 9800 (R350 4E49), RADEON 9800 XT (R360 4E4A),
	FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), FireGL V3100 (RV370 5B64),
	FireMV 2200 (RV370 5B65), MOBILITY RADEON X300 (M22 5460),
	MOBILITY FireGL V3100 (M22 5464), RADEON X600 (RV380 3E50),
	FireGL V3200 (RV380 3E54), MOBILITY RADEON X600 (M24 3150),
	MOBILITY RADEON X300 (M22 3152), MOBILITY FireGL V3200 (M24 3154),
	RADEON X800 (R420 4A48), RADEON X800 PRO (R420 4A49),
	RADEON X800 SE (R420 4A4A), RADEON X800 XT (R420 4A4B),
	RADEON X800 (R420 4A4C), FireGL X3-256 (R420 4A4D),
	MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 XT Platinum Edition (R420 4A50), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 SE (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	RADEON X800 XL (R430 554D), RADEON X800 (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X850 PRO (R480 5D4F), RADEON X850 XT (R480 5D52),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), MOBILITY RADEON X700 XL,
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	FireGL (R520 7105), RADEON X900 (R520 7109)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.18.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.18g2                           
(II) ATI Proprietary Linux Driver Build Date: Oct 25 2005 10:35:14
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.18.1-driver-lnx-221930
(--) Chipset MOBILITY RADEON 9600/9700 (M10/M11 4E50) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfaffc000 - 0xfaffcfff (0x1000) MX[B]
	[6] -1	0	0xfaff8000 - 0xfaffbfff (0x4000) MX[B]
	[7] -1	0	0xfaffd800 - 0xfaffdfff (0x800) MX[B]
	[8] -1	0	0xfaffe000 - 0xfaffffff (0x2000) MX[B]
	[9] -1	0	0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
	[10] -1	0	0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
	[11] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[12] -1	0	0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0x80000000 - 0x8001ffff (0x20000) MX[B](B)
	[15] -1	0	0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b080 - 0x0000b0ff (0x80) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[21] -1	0	0x0000bc40 - 0x0000bc7f (0x40) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[29] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[30] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x82106e8
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfaffc000 - 0xfaffcfff (0x1000) MX[B]
	[6] -1	0	0xfaff8000 - 0xfaffbfff (0x4000) MX[B]
	[7] -1	0	0xfaffd800 - 0xfaffdfff (0x800) MX[B]
	[8] -1	0	0xfaffe000 - 0xfaffffff (0x2000) MX[B]
	[9] -1	0	0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
	[10] -1	0	0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
	[11] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[12] -1	0	0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0x80000000 - 0x8001ffff (0x20000) MX[B](B)
	[15] -1	0	0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b080 - 0x0000b0ff (0x80) IX[B]
	[23] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[24] -1	0	0x0000bc40 - 0x0000bc7f (0x40) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[26] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[32] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[33] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[34] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "MonitorLayout" "AUTO,NONE"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(WW) fglrx(0): Bad V_BIOS checksum
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(--) fglrx(0): Chipset: "MOBILITY RADEON 9600/9700 (M10/M11 4E50)" (Chipset = 0x4e50)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x2001)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfcff0000
(--) fglrx(0): ROM-BIOS at 0x80000000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131008 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON 9600   
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: P10 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): Video RAM override, using 131072 kB instead of 131072 kB
(**) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): MonitorLayout is no longer supported. 
               Please use DesktopSetup and ForceMonitors options
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 3155  Serial#: 0
(II) fglrx(0): Year: 2003  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 161.8 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1920  h_sync: 2020  h_sync_end 2052 h_blank_end 2184 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1202  v_sync_end 1208 v_blanking: 1235 v_border: 0
(II) fglrx(0):  W3866154U1
(II) fglrx(0):  º¯&#158;&#142;r`@
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 18 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1200 (pitch 1920)
(**) fglrx(0): *Mode "1920x1200": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1200"  161.75  1920 2016 2048 2184  1200 1202 1208 1235
(**) fglrx(0): *Mode "1600x1200": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  161.75  1600 1856 1888 2184  1200 1202 1208 1235
(**) fglrx(0): *Mode "1280x1024": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  161.75  1280 1696 1728 2184  1024 1114 1120 1235
(**) fglrx(0): *Mode "1024x768": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  161.75  1024 1568 1600 2184  768 986 992 1235
(**) fglrx(0): *Mode "800x600": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  161.75  800 1456 1488 2184  600 902 908 1235
(**) fglrx(0): *Mode "640x480": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  161.75  640 1376 1408 2184  480 842 848 1235
(**) fglrx(0):  Default mode "1680x1050": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"  161.75  1680 1896 1928 2184  1050 1127 1133 1235 +csync
(**) fglrx(0):  Default mode "1280x800": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"  161.75  1280 1696 1728 2184  800 1002 1008 1235 +csync
(**) fglrx(0):  Default mode "1280x768": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"  161.75  1280 1696 1728 2184  768 986 992 1235 +csync
(**) fglrx(0):  Default mode "848x480": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"  161.75  848 1480 1512 2184  480 842 848 1235 +csync
(**) fglrx(0):  Default mode "720x576": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"  161.75  720 1416 1448 2184  576 890 896 1235 +csync
(**) fglrx(0):  Default mode "720x480": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  161.75  720 1416 1448 2184  480 842 848 1235 +csync
(**) fglrx(0):  Default mode "640x400": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  161.75  640 1376 1408 2184  400 802 808 1235 -hsync
(**) fglrx(0):  Default mode "640x350": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"  161.75  640 1376 1408 2184  350 777 783 1235 -hsync +csync
(**) fglrx(0):  Default mode "512x384": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  161.75  512 1312 1344 2184  384 794 800 1235 -hsync
(**) fglrx(0):  Default mode "400x300": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  161.75  400 1256 1288 2184  600 902 908 1235 -hsync
(**) fglrx(0):  Default mode "320x240": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  161.75  320 1216 1248 2184  480 842 848 1235 -hsync
(**) fglrx(0):  Default mode "320x200": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  161.75  320 1216 1248 2184  400 802 808 1235 -hsync
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (147, 145)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.18.8
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): cpuSpeedMHz: 0x00000256
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfcff0000 - 0xfcffffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfaffc000 - 0xfaffcfff (0x1000) MX[B]
	[8] -1	0	0xfaff8000 - 0xfaffbfff (0x4000) MX[B]
	[9] -1	0	0xfaffd800 - 0xfaffdfff (0x800) MX[B]
	[10] -1	0	0xfaffe000 - 0xfaffffff (0x2000) MX[B]
	[11] -1	0	0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
	[12] -1	0	0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
	[13] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[14] -1	0	0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
	[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[16] -1	0	0x80000000 - 0x8001ffff (0x20000) MX[B](B)
	[17] -1	0	0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] 0	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000b080 - 0x0000b0ff (0x80) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[27] -1	0	0x0000bc40 - 0x0000bc7f (0x40) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[29] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[30] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[31] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[32] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[35] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[36] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): UMM Bus area:     0xd0acb000 (size=0x07535000)
(II) fglrx(0): UMM area:     0xd0acb000 (size=0x07535000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023

drmOpenDevice: node name is /dev/dri/card251
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card252
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card253
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8dab000
(II) fglrx(0): [drm] mapped SAREA 0xf8dab000 to 0xb7ac4000
(II) fglrx(0): [drm] framebuffer handle = 0xd0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.18.8
(II) fglrx(0):     Date: Oct 25 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-9-686
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfcff0000
(II) fglrx(0): [agp] Mode=0x1f000217 bridge: 0x8086/0x3340
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000314
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000314)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xf8f81000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x00acb000
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,1473)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1200)
(II) fglrx(0): Largest offscreen area available: 1920 x 265
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "UseInternalAGPART" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
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

---

### Post by mlomker on 2005-11-06
> And dmesg | grep fglrx  don't say nothing :S


You need to run it a bit sooner after bootup.  I didn't see any errors in the Xorg log.  Try **sudo fglrxinfo** to see if it gives you something different.

---

### Post by hed on 2005-11-06
Here is dmesg | grep fglrx:
> [4294691.536000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294691.537000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[4294691.537000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
[4294727.036000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294727.037000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294727.037000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294727.037000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294727.038000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294727.167000] [fglrx] free  AGP = 121909248
[4294727.167000] [fglrx] max   AGP = 121909248
[4294727.167000] [fglrx] free  LFB = 104345600
[4294727.167000] [fglrx] max   LFB = 104345600
[4294727.167000] [fglrx] free  Inv = 0
[4294727.167000] [fglrx] max   Inv = 0
[4294727.167000] [fglrx] total Inv = 0
[4294727.167000] [fglrx] total TIM = 0
[4294727.167000] [fglrx] total FB  = 0
[4294727.167000] [fglrx] total AGP = 32768

And here fglrxinfo -v:
> display: :0.0  screen:0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glx server vendor string: SGI
glx server version string: 1.2
glx server extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
glx client version: 1.4
glx client extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig

Visual ID: 23  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 24  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 25  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 26  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 27  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 28  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 29  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 2a  depth=24  class=TrueColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 2b  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 2c  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 2d  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 2e  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=16 greenSize=16 blueSize=16 alphaSize=16
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 2f  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 30  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=8
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 31  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=1 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    Opaque.
Visual ID: 32  depth=24  class=DirectColor
    bufferSize=32 level=0 renderType=rgba doubleBuffer=0 stereo=0
    rgba: redSize=8 greenSize=8 blueSize=8 alphaSize=8
    auxBuffers=0 depthSize=24 stencilSize=0
    accum: redSize=0 greenSize=0 blueSize=0 alphaSize=0
    multiSample=0  multiSampleBuffers=0
    Opaque.

---

