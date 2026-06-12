---
title: "help! update broke my xorg.conf (ATI radeon)"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by ischg on 2006-08-21
I installed dapper on my new notebook successfully, but after having it run for a day (with several successful reboots), the update of "xserver-xorg-core" that became available today broke my xorg.conf (could be that it wasn't set up properly, but still worked :-k ). I get the "(EE) No devices detected"/"No screens found" error (see below)
Here is the Xorg.0.log...
```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux thinkpad 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 21 22:23:19 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. ATI Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: Found 0 domains.
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 17aa,2015 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 17aa,2010 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 17aa,200a rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 17aa,200a rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 17aa,200a rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 17aa,200a rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 17aa,200b rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 17aa,2009 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 17aa,200c rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 17aa,200d rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 17aa,200f rev 02 class 0c,05,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xee100000 - 0xee1fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xee000000 - 0xee0fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
	[4] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[5] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[6] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[7] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe40fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:2), (0,4,11), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[1] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[2] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[3] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
	[4] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[5] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[6] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[7] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe9ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xe4100000 - 0xe41fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:3), (0,12,19), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 12 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[4] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[5] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[6] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[7] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xea000000 - 0xebffffff (0x2000000) MX[B]
(II) Bus 12 prefetchable memory range:
	[0] -1	0	0xe4200000 - 0xe42fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 21: bridge is at (0:30:0), (0,21,25), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 21 I/O range:
	[0] -1	0	0x0000a000 - 0x0000dfff (0x4000) IX[B]
(II) Bus 21 non-prefetchable memory range:
	[0] -1	0	0xe4300000 - 0xe7ffffff (0x3d00000) MX[B]
(II) Bus 21 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xee404400 - 0xee4047ff (0x400) MX[B]
	[1] -1	0	0xee404000 - 0xee4043ff (0x400) MX[B]
	[2] -1	0	0xee400000 - 0xee403fff (0x4000) MX[B]
	[3] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[4] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[5] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[6] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[7] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[8] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[9] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[10] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xee404400 - 0xee4047ff (0x400) MX[B]
	[1] -1	0	0xee404000 - 0xee4043ff (0x400) MX[B]
	[2] -1	0	0xee400000 - 0xee403fff (0x4000) MX[B]
	[3] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[4] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[5] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[6] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[7] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[8] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[9] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[10] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xee404400 - 0xee4047ff (0x400) MX[B]
	[5] -1	0	0xee404000 - 0xee4043ff (0x400) MX[B]
	[6] -1	0	0xee400000 - 0xee403fff (0x4000) MX[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[9] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[10] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[11] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[12] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[13] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[14] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[15] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[16] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[17] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[18] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.25.18
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9000 (RV280 5962),
	RADEON 9200 SE (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), RADEON X850 XT (R480 5D52),
	RADEON X850 (R481 4B48), RADEON X850 XT (R481 4B49),
	RADEON X850 SE (R481 4B4A), RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
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
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 XT (R520 7108),
	RADEON X1800 PRO (R520 7109), RADEON X1800 SE (R520 710A),
	RADEON X1800 (R520 710B), RADEON X1800 (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	RADEON X1300 PRO (RV505 7143), RADEON X1300 (RV505 7147),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1300 (RV505 715F), RADEON X1300 XT (RV515 7140),
	RADEON X1300 PRO (RV515 7142), MOBILITY FireGL (M54 GL 7144),
	MOBILITY RADEON X1400 (M54 7145), RADEON X1300 LE (RV515 7146),
	MOBILITY RADEON X1300 (M52 7149), MOBILITY RADEON X1300 (M52 714A),
	RADEON X1300 SE (RV515 714E), FireGL V3300 (RV515 7152),
	RADEON X1300 VE (RV515 715E), RADEON X1300 (RV516 7180),
	RADEON X1300 (RV516 7183), RADEON X1300 (RV516 7187),
	RADEON X1900 (R580 7240), RADEON X1900 (R580 7243),
	RADEON X1900 (R580 7244), RADEON X1900 (R580 7245),
	RADEON X1900 (R580 7246), RADEON X1900 (R580 7247),
	RADEON X1900 (R580 7248), RADEON X1900 (R580 7249),
	RADEON X1900 (R580 724A), RADEON X1900 (R580 724B),
	RADEON X1900 (R580 724C), RADEON X1900 (R580 724D),
	RADEON X1900 (R580 724E), RADEON X1900 (R580 724F),
	RADEON X1600 XT (RV530 71C0), RADEON X1600 PRO (RV530 71C2),
	MOBILITY FireGL V5200 (M56 71C4), MOBILITY RADEON X1600 (M56 71C5),
	RADEON (RV530 LE 71C6), RADEON (RV530 VE 71CE),
	FireGL V3400 (RV530 71D2), FireGL V5200 (RV530 71DA),
	RADEON (RV530 SE 71DE)
(II) ATI Proprietary Linux Driver Version Identifier:8.25.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.25g1                           
(II) ATI Proprietary Linux Driver Build Date: May 18 2006 09:54:44
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.25.1-driver-lnx-268237
(EE) No devices detected.

Fatal server error:
no screens found

```
And my xorg.conf is ...
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"				# was "vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I was initially running my machine on vesa, and switched to fglrx after the xserver hiccup (I already had installed the xorg-driver-fglrx/fglrx-control packages). I also tried to run
# dpkg-reconfigure xserver-xorg
but to no avail. I'd really appreciate your help, thanks!

And, before I forget, my graphics chip is the ATI radeon mobility x1400

---

### Post by jimmysz on 2006-08-21
Try
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

This will revert to the previous working update.

---

### Post by mgpower0 on 2006-08-21
happening to everyone today. If you haven't already read try 
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
sudo /etc/init.d/gdm restart

hope it works for you

---

### Post by nofreerides on 2006-08-21
Copy that!  I had the same problem ](*,) 
and this worked for me also:
--------------------------------
Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 
-----------------------

---

### Post by ischg on 2006-08-22
that totally worked. thanks for this extremely fast response! I really appreciate it.
Btw, is there a bug report out yet? Malone seems to be offline ...

---

### Post by Dropknee on 2006-08-22
This happen to me right now, the update broke my xorg.conf and the system send me to console, so I switch to Windows to find a solution and for my surprise the community responds once again :D

---

### Post by Dropknee on 2006-08-22
Ok im back in Ubuntu box, Thx to all for this quick fix

---

### Post by JasonPN on 2006-08-22
I had a similar problem too as I was working on a box for a new classroom setup.  I am playing around with different video cards (and will post a question elsewhere... :) ) but I wonder...will this be fixed at some point so we can update to the new version without it boinking our systems?

---

### Post by Dropknee on 2006-08-22
I dont know is this is a problem with the update, but I cant update compiz-gnome with the new version

```
E: /var/cache/apt/archives/compiz-gnome_0.0.13.35_i386.deb: trying to overwrite `/usr/share/gnome/wm-properties/compiz.desktop', which is also in package compiz
```

anyone have the same issue???

---

### Post by Dropknee on 2006-08-22
ok apparently they remove the new compiz-gnome from repo, I update the repo and the compiz-gnome update disappear. Sorry for the off topic

---

### Post by mbradlcu on 2006-08-22
wow, thanks for the fix! BTW here's the deviation I found from an old Xorg.2.log compared to the new failed output:

working output
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV40 [GeForce 6800] rev 161, Mem @ 0xce000000/24, 0xc0000000/27, 0xcd000000/24, BIOS @ 0xcfee0000/17
(II) Bus 1 non-prefetchable memory range:

borked
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:

for what ever xserver isn't finding the video card

---

### Post by euxneks on 2006-08-22
Just wanted to first post to confirm that the latest update breaks my xserver. Says "No Screen" &tc.  I am using Nvidia, not ATI - so it's a problem with the update.

Was able to fix the problem with the posted solution.

---

### Post by t800t8 on 2006-08-22
Sorry but how can I install if I don't have Internet connection? I try to run

> sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

but it cannot fetch DEB file from [http://archive.ubuntu.com](http://archive.ubuntu.com)

Thanks

---

### Post by t800t8 on 2006-08-22
Fix it myself.

Download [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_i386.deb) then run

> sudo dpkg -i xserver-xorg-core_1.0.2-0ubuntu10_i386.deb

But I still have problem. My monitor is wide screen (1200 x 800) but downgrade by xserver-xorg-core_1.0.2-0ubuntu10_i386.deb only supports 640 x 480, 800 x 600 and 1024 x 768. How can I fix it? Thanks

---

### Post by Macchi on 2006-08-22
I had also the same problem in which the latest upgrade broke the X server. The workaround was to manually downgrade the package xserver-xorg-core on the command line. This was the most serious Linux incident for me since I've started using exclusively Linux on my desktops and servers about a year ago. In the future I have to be more conservative about upgrades, applying them first on a test machine.

[B]Remenber to lock the current version of xserver-xorg-core in Synaptic to avoid accidental upgrades while we wait for a definitive solution. In Synaptic Search for xserver-xorg-core, select it, and then choose Package->Lock Version.
[/B]



Is there a good way to perform _automatic_ roll back of installed software?

---

### Post by quad3d@work on 2006-08-22
Not to be a troll... but this is one of the whys I still don't use Linux as main desktop OS. Simple package update breaks my whole system for what?!

Thanks for the fix, works great.

---

### Post by househead on 2006-08-22
This broke my setup too (Nvidia).

Thanks guys for heads-up on a fix.

Why the hell are updates being pushed out that breaks X!?

This is supposed to be a stable release.

What a FU(KUP! :evil:

---

### Post by t800t8 on 2006-08-22
Fix it myself with

> sudo dpkg-reconfigure xserver-xorg

:-)

---

### Post by tseliot on 2006-08-22
The solution (with the latest package):
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by ubuntu_demon on 2006-08-22
I've closed this thread. 

Let's keep this discussion in one place :
[B]
PLEASE READ: The Latest Updates Break the Xserver!
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)[/B]

---

