---
title: "Dual Monititor with S3Virge (module unload)"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by computergeekxp on 2007-07-11
I am currently running feisty with an nvidia geforce 2 and a s3virge video card. I have edited my xorg file so that both these monitors can be used as separate screens but it's a no go with the s3virge (Although it does work with win-xp). The monitor on the s3virge stays black, aside from the terminal output on boot and in the other terminals(ctrl_alt+f3...).

When looking at the xorg log file, it appears that the s3virge module is being unloaded after the  s3virge and nvidia modules are loaded. Could some one explain why it automatically unloads? Thanks.

Xorg Log Snippet
```
(II) UnloadModule: "s3virge"
(II) Unloading /usr/lib/xorg/modules/drivers//s3virge_drv.so

```

Xorg Log
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Mike 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 11 11:25:33 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "nvidia"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "lcd"
(**) |   |-->Device "virge"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "on"
(**) Xinerama: enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2530 card 1028,00c7 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2532 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 1028,00c7 rev 04 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 1028,00c7 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 1028,00c7 rev 04 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 1028,00c7 rev 04 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0110 card 10de,0091 rev b2 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 168c,0013 card 1948,3a02 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:08:0: chip 1033,00cd card 12ee,8011 rev 01 class 0c,00,10 hdr 00
(II) PCI: 02:09:0: chip 10ec,8139 card 11ad,3104 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0a:0: chip 1274,1371 card 1274,1371 rev 09 class 04,01,00 hdr 00
(II) PCI: 02:0b:0: chip 5333,8a01 card 5333,8a01 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[1] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[2] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[3] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xfbffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (1:0:0) nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 178, Mem @ 0xfc000000/24, 0xe8000000/27
(--) PCI:*(2:11:0) S3 Inc. ViRGE/DX or /GX rev 1, Mem @ 0xf4000000/26, BIOS @ 0x80000000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfbeeec00 - 0xfbeeecff (0x100) MX[B]
	[1] -1	0	0xfbeef000 - 0xfbeeffff (0x1000) MX[B]
	[2] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0x80000000 - 0x8000ffff (0x10000) MX[B](B)
	[5] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[6] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[9] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[10] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[11] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[12] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfbeeec00 - 0xfbeeecff (0x100) MX[B]
	[1] -1	0	0xfbeef000 - 0xfbeeffff (0x1000) MX[B]
	[2] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B]
	[3] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[4] -1	0	0x80000000 - 0x8000ffff (0x10000) MX[B](B)
	[5] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[6] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[9] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[10] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[11] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[12] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[4] -1	0	0xfbeeec00 - 0xfbeeecff (0x100) MX[B]
	[5] -1	0	0xfbeef000 - 0xfbeeffff (0x1000) MX[B]
	[6] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0x80000000 - 0x8000ffff (0x10000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[16] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[17] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[18] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "s3virge"
(II) Loading /usr/lib/xorg/modules/drivers//s3virge_drv.so
(II) Module s3virge: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) S3VIRGE: driver (version 1.9.1) for S3 ViRGE chipsets: virge, 86C325,
	virge vx, 86C988, virge dx, virge gx, 86C375, 86C385, virge gx2,
	86C357, virge mx, 86C260, virge mx+, 86C280, trio 3d, 86C365,
	trio 3d/2x, 86C362, 86C368
(II) Primary Device is: PCI 02:0b:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbeeec00 - 0xfbeeecff (0x100) MX[B]
	[5] -1	0	0xfbeef000 - 0xfbeeffff (0x1000) MX[B]
	[6] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0x80000000 - 0x8000ffff (0x10000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[16] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[17] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[18] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(WW) S3VIRGE: No matching Device section for instance (BusID PCI:2:11:0) found
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbeeec00 - 0xfbeeecff (0x100) MX[B]
	[5] -1	0	0xfbeef000 - 0xfbeeffff (0x1000) MX[B]
	[6] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0x80000000 - 0x8000ffff (0x10000) MX[B](B)
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[18] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[19] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[20] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[21] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.1, 1.1, 1.1)
(**) NVIDIA(0): Option "MetaModes" "1280x1024_85 +0+0; 1024x768_85 +0+0; 1280x1024 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
(**) NVIDIA(0): Option "TripleBuffer" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 MX/MX 400 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.01.30.63
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 MX/MX 400 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     DELL  M991 (CRT-0)
(--) NVIDIA(0): DELL  M991 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024_85+0+0"
(II) NVIDIA(0):     "1024x768_85+0+0"
(II) NVIDIA(0):     "1280x1024+0+0"
(II) NVIDIA(0):     "1024x768+0+0"
(II) NVIDIA(0):     "800x600+0+0"
(II) NVIDIA(0):     "640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (90, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(II) UnloadModule: "s3virge"
(II) Unloading /usr/lib/xorg/modules/drivers//s3virge_drv.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfbeeec00 - 0xfbeeecff (0x100) MX[B]
	[7] -1	0	0xfbeef000 - 0xfbeeffff (0x1000) MX[B]
	[8] -1	0	0xfbef0000 - 0xfbefffff (0x10000) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0x80000000 - 0x8000ffff (0x10000) MX[B](B)
	[11] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[22] -1	0	0x0000dcd0 - 0x0000dcdf (0x10) IX[B]
	[23] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024_85+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Mouse0: Device: "/dev/input/mice"
(**) Mouse0: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Buttons" "7"
(==) Mouse0: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5 6 7"
(**) Mouse0: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Mouse0: Buttons: 11
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Mouse0: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1280x1024_85+0+0"
(II) Mouse0: ps2EnableDataReporting: succeeded
AUDIT: Wed Jul 11 11:53:01 2007: 6236 X: client 38 rejected from local host (uid 0)
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Wed Jul 11 11:53:02 2007: 6236 X: client 38 rejected from local host (uid 0)
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1

```

Xorg Conf
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
  Identifier "Layout0"
  Screen 0 "Screen0"
  Screen 1 "Screen1" RightOf "Screen0"
  InputDevice "Keyboard0" "CoreKeyboard"
  InputDevice "Mouse0" "CorePointer"
  Option "Xinerama" "on"
EndSection

Section "Files"
  RgbPath "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
  Load "extmod"
  Load "type1"
  Load "freetype"
  load "glx"
  load "v4l"
EndSection

Section "ServerFlags"
EndSection

Section "InputDevice"
  Identifier "Mouse0"
  Driver "mouse"
  option "core pointer"
  option "DEVICE" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "Buttons" "7"
  option "ZAxisMapping" "4 5 6 7"
EndSection

Section "InputDevice"
  Identifier "Mouse1"
  Driver "evdev"
  option "Device" "/dev/input/event1"
EndSection

Section "InputDevice"
  # generated from default
  Identifier "Keyboard0"
  Driver "kbd"
EndSection

Section "Monitor"
  identifier "Monitor0"
  vendorname "Unknown"
  modelname "DELL  M991"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
  gamma 1.12
EndSection

Section "Monitor"
Identifier "lcd"
Option "DPMS"
HorizSync 30-65
VertRefresh 50-75
EndSection

Section "Device"
  identifier "nvidia"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nvidia"
  screen 0
    Option "TripleBuffer" "True"
EndSection

Section "Device"
Identifier "virge"
Driver "s3virge"
BusID "PCI:2:0b:0"
Option "BusType" "PCI"
Option "RenderAccel" "true"
Option "OpenGLOverlay" "1"
Option "EnablePageFlip" "true"
Option "MergedFB" "On"
EndSection

Section "Screen"
    option "AddARGBGLXVisuals" "True"
    Identifier     "Screen0"
    Device         "nvidia"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024_85 +0+0; 1024x768_85 +0+0; 1280x1024 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    option "AddARGBGLXVisuals" "True"
    Identifier     "Screen1"
    Device         "virge"
    Monitor        "lcd"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

-Mike

---

