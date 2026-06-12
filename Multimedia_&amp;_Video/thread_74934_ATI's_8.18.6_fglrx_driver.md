---
title: "ATI's 8.18.6 fglrx driver"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by jiahanhao on 2005-10-13
Running mobility x800 with x86_64 breezy, using latest ATI driver 8.18.6

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 root@crested.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF] 
Current Operating System: Linux sager 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:27:39 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 12 20:07:37 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Mobility X800 (R430)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 1558,0700 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2581 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,2668 card 1558,0700 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1558,0700 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1558,0700 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1558,0700 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1558,0700 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1558,0700 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2640 card 1558,0700 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1558,0700 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 1558,0700 rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 1558,0700 rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5d4a card 1558,0700 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4362 card 1558,0700 rev 19 class 02,00,00 hdr 00
(II) PCI: 0a:00:0: chip 104c,ac54 card 6400,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 0a:00:1: chip 104c,ac54 card 6c00,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 0a:00:2: chip 104c,8201 card 1558,0700 rev 01 class 08,80,00 hdr 00
(II) PCI: 0a:01:0: chip 104c,8026 card 1558,0700 rev 00 class 0c,00,10 hdr 00
(II) PCI: 0a:05:0: chip 1814,0201 card 1462,6833 rev 01 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,15), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xb0100000 - 0xb01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[1] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[2] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[3] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xb0200000 - 0xb02fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 10: bridge is at (0:30:0), (0,10,10), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 10 I/O range:
	[0] -1	0	0x00006000 - 0x00006fff (0x1000) IX[B]
(II) Bus 10 non-prefetchable memory range:
	[0] -1	0	0xb0300000 - 0xb03fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 11: bridge is at (10:0:0), (10,11,14), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 11 I/O range:
	[0] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[1] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 15: bridge is at (10:0:1), (10,15,18), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 15 I/O range:
	[0] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x5d4a) rev 0, Mem @ 0xc0000000/28, 0xb0100000/16, I/O @ 0x4000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xb0304000 - 0xb0305fff (0x2000) MX[B]
	[1] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[2] -1	0	0xb0306000 - 0xb03067ff (0x800) MX[B]
	[3] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[4] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[5] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[6] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[9] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[10] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[11] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[12] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[13] -1	0	0x000030b8 - 0x000030bb (0x4) IX[B]
	[14] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[15] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[16] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[17] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[18] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[20] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb0304000 - 0xb0305fff (0x2000) MX[B]
	[1] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[2] -1	0	0xb0306000 - 0xb03067ff (0x800) MX[B]
	[3] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[4] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[5] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[6] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[9] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[10] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[11] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[12] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[13] -1	0	0x000030b8 - 0x000030bb (0x4) IX[B]
	[14] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[15] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[16] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[17] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[18] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[20] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xb0304000 - 0xb0305fff (0x2000) MX[B]
	[6] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[7] -1	0	0xb0306000 - 0xb03067ff (0x800) MX[B]
	[8] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[9] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[16] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[17] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[18] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[19] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[20] -1	0	0x000030b8 - 0x000030bb (0x4) IX[B]
	[21] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[22] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[23] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[24] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[25] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[27] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
	[28] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
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
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.18.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) ATI Radeon/FireGL: The following chipsets are supported:
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
(II) ATI Proprietary Linux Driver Version Identifier:8.18.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.18g1                           
(II) ATI Proprietary Linux Driver Build Date: Oct 11 2005 10:57:22
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.18.1-driver-lnx-x86_64-218592
(**) ChipID override: 0x5D48
(**) Chipset MOBILITY RADEON X800 XT (M28 5D48) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xb0304000 - 0xb0305fff (0x2000) MX[B]
	[6] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[7] -1	0	0xb0306000 - 0xb03067ff (0x800) MX[B]
	[8] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[9] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[16] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[17] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[18] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[19] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[20] -1	0	0x000030b8 - 0x000030bb (0x4) IX[B]
	[21] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[22] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[23] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[24] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[25] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[26] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[27] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
	[28] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x71a870
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xb0304000 - 0xb0305fff (0x2000) MX[B]
	[6] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[7] -1	0	0xb0306000 - 0xb03067ff (0x800) MX[B]
	[8] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[9] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[10] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[11] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[12] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[19] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[20] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[21] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[22] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[23] -1	0	0x000030b8 - 0x000030bb (0x4) IX[B]
	[24] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[25] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[26] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[27] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[28] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[30] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
	[31] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
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
(**) fglrx(0): Option "Capabilities" "0x00000000"
(**) fglrx(0): Option "CapabilitiesEx" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionI" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionII" "0x00000000"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DesktopSetup" "(null)"
(**) fglrx(0): Option "ScreenOverlap" "0"
(**) fglrx(0): Option "UseInternalAGPGART" "yes"
(**) fglrx(0): Option "Stereo" "off"
(**) fglrx(0): Option "StereoSyncEnable" "1"
(**) fglrx(0): Option "UseFastTLS" "0"
(**) fglrx(0): Option "BlockSignalsOnLock" "on"
(**) fglrx(0): Option "ForceGenericCPU" "no"
(**) fglrx(0): Option "CenterMode" "off"
(**) fglrx(0): Option "FSAAScale" "1"
(**) fglrx(0): Option "FSAAEnable" "no"
(**) fglrx(0): Option "FSAADisableGamma" "no"
(**) fglrx(0): Option "FSAACustomizeMSPos" "no"
(**) fglrx(0): Option "FSAAMSPosX0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX5" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY5" "0.000000"
(**) fglrx(0): Option "PseudoColorVisuals" "off"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x00000000
(**) fglrx(0): Gamma Correction for II is 0x00000000
(==) fglrx(0): Buffer Tiling is ON
(**) fglrx(0): Option "mtrr" "off"
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Chipset: "MOBILITY RADEON X800 XT (M28 5D48)" (Chipset = 0x5d48)
(**) fglrx(0): (PciSubVendor = 0x1558, PciSubDevice = 0x0700)
(**) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xb0100000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 262080 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON X800(M28) XT
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: M28
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(--) fglrx(0): VideoRAM: 131072 kByte, Type: UNKNOWN
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MS_  Model: 0  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:Serration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 60  vid: 16497
(II) fglrx(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #5: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 161.8 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2040 h_blank_end 2184 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1200  v_sync_end 1200 v_blanking: 1235 v_border: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(**) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(**) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 19 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1200 (pitch 1920)

```

---

### Post by jiahanhao on 2005-10-13
```


(**) fglrx(0): *Mode "1920x1200": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1200"  161.75  1920 2008 2040 2184  1200 1201 1207 1235
(**) fglrx(0):  Default mode "1600x1200": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  161.75  1600 1848 1880 2184  1200 1201 1207 1235
(**) fglrx(0):  Default mode "1400x1050": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"  161.75  1400 1744 1776 2184  1050 1126 1132 1235 +csync
(**) fglrx(0):  Default mode "1280x1024": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  161.75  1280 1688 1720 2184  1024 1113 1119 1235
(**) fglrx(0):  Default mode "1280x800": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"  161.75  1280 1688 1720 2184  800 1001 1007 1235 +csync
(**) fglrx(0):  Default mode "1280x768": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"  161.75  1280 1688 1720 2184  768 985 991 1235 +csync
(**) fglrx(0):  Default mode "1152x864": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"  161.75  1152 1624 1656 2184  864 1033 1039 1235
(**) fglrx(0):  Default mode "1024x768": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"  161.75  1024 1560 1592 2184  768 985 991 1235
(**) fglrx(0):  Default mode "848x480": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"  161.75  848 1472 1504 2184  480 841 847 1235 +csync
(**) fglrx(0):  Default mode "800x600": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"  161.75  800 1448 1480 2184  600 901 907 1235
(**) fglrx(0):  Default mode "720x576": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"  161.75  720 1408 1440 2184  576 889 895 1235 +csync
(**) fglrx(0):  Default mode "720x480": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"  161.75  720 1408 1440 2184  480 841 847 1235 +csync
(**) fglrx(0):  Default mode "640x480": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"  161.75  640 1368 1400 2184  480 841 847 1235
(**) fglrx(0):  Default mode "640x400": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"  161.75  640 1368 1400 2184  400 801 807 1235 -hsync
(**) fglrx(0):  Default mode "640x350": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"  161.75  640 1368 1400 2184  350 776 782 1235 -hsync +csync
(**) fglrx(0):  Default mode "512x384": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"  161.75  512 1304 1336 2184  384 793 799 1235 -hsync
(**) fglrx(0):  Default mode "400x300": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"  161.75  400 1248 1280 2184  600 901 907 1235 -hsync
(**) fglrx(0):  Default mode "320x240": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"  161.75  320 1208 1240 2184  480 841 847 1235 -hsync
(**) fglrx(0):  Default mode "320x200": 161.8 MHz (scaled from 0.0 MHz), 74.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"  161.75  320 1208 1240 2184  400 812 818 1235 -hsync
(--) fglrx(0): Display dimensions: (400, 300) mm
(--) fglrx(0): DPI set to (121, 101)
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
(**) fglrx(0): FSAA Gamma enabled
(**) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.18.6
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00000000
(**) fglrx(0): CapabilitiesEx: 0x00000000
(**) fglrx(0): cpuFlags: 0x8000001d
(**) fglrx(0): cpuSpeedMHz: 0x00000bb8
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): UseFastTLS=0
(**) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xb0100000 - 0xb010ffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xb0304000 - 0xb0305fff (0x2000) MX[B]
	[8] -1	0	0xb0300000 - 0xb0303fff (0x4000) MX[B]
	[9] -1	0	0xb0306000 - 0xb03067ff (0x800) MX[B]
	[10] -1	0	0xb0200000 - 0xb0203fff (0x4000) MX[B]
	[11] -1	0	0xb0004000 - 0xb00043ff (0x400) MX[B]
	[12] -1	0	0xb0000000 - 0xb0003fff (0x4000) MX[B]
	[13] -1	0	0xb0100000 - 0xb010ffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] 0	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[22] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[23] -1	0	0x00003090 - 0x0000309f (0x10) IX[B]
	[24] -1	0	0x000030a4 - 0x000030a7 (0x4) IX[B]
	[25] -1	0	0x000030b0 - 0x000030b7 (0x8) IX[B]
	[26] -1	0	0x000030b8 - 0x000030bb (0x4) IX[B]
	[27] -1	0	0x000030c0 - 0x000030c7 (0x8) IX[B]
	[28] -1	0	0x00003080 - 0x0000308f (0x10) IX[B]
	[29] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[30] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[31] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[33] -1	0	0x00004000 - 0x000040ff (0x100) IX[B](B)
	[34] -1	0	0x00006000 - 0x0000603f (0x40) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): UMM Bus area:     0xc0acb000 (size=0x07525000)
(II) fglrx(0): UMM area:     0xc0acb000 (size=0x07525000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x07ff0000
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1200)
(II) fglrx(0): Largest offscreen area available: 1920 x 6988
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) Synaptics touchpad driver version 0.13.6
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event1
(**) Option "Device" "/dev/input/event1"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad synaptics touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad synaptics touchpad found
Synaptics DeviceOff called

```

---

### Post by mlomker on 2005-10-13
> 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


The dri problem was common with the older drivers, but you'd think it'd be solved by now.  The old fix for 32-bit Ubuntu was to download a fixed dri file and overwrite.  Those instructions are in my [how-to]("http://www.ubuntuforums.org/showthread.php?p=348911").

I want you to double-check that you have the **linux-restricted-*** package removed.  Having it installed makes it impossible to install ATI's packaged drivers because they'll constantly be overwritten by the Breezy version.  

I'm also curious why you didn't use 8.16.20?  I'm not aware of any serious problems.  The new 8.18.6 driver primarily fixes the dri (monitor resolution detection) problem for certain monitors and doesn't offer better performance or features.

I installed the driver.  Here's the problem that I ran into:

```

Fatal server error:
could not open default font 'fixed';
the X server's font paths might be misconfigured, remote font server(s)
may be unreachable, and/or local fonts may not be installed or are not
configured correctly.

```

I fixed it by commenting out (#) every font line in my xorg.conf file.  It appears to work fine now.  I'm not sure what has changed between 8.16.20 and the new driver but there's something it doesn't like about Breezy's fonts--even after reconfiguring with ATI's **fglrxconfig**.

---

### Post by Cred on 2005-10-13
[QUOTE=mlomker]
I fixed it by commenting out (#) every font line in my xorg.conf file.  It appears to work fine now.  I'm not sure what has changed between 8.16.20 and the new driver but there's something it doesn't like about Breezy's fonts--even after reconfiguring with ATI's **fglrxconfig**.[/QUOTE]
Not sure but [http://ubuntuforums.org/showpost.php?p=337950&postcount=2]("http://ubuntuforums.org/showpost.php?p=337950&postcount=2") this helped me, could be that it's just ignoring the new path just like by commenting them out.

---

### Post by mlomker on 2005-10-13
>  this helped me, could be that it's just ignoring the new path just like by commenting them out.

Thanks, I'll take a look.  The fonts look fine while commented out, so I'm not concerned about that.

The problem that I'm having now is that there doesn't seem to be any way of getting rid of MESA in Breezy.  I have an fglrx display at the proper resolution now but fps is like 180.  :( 

I can only pray that someone decides to put the new package into the Breezy repos and doesn't make me wait for Drake.  The dri/resolution problem with 8.16.20 is a killer for me.  I'm stuck with the ATI driver unless I can figure out how to get ATI's 8.18.6 package to install.  I haven't given up yet, but I've already burned 4 hours on it today.

---

### Post by darknuala on 2005-10-13
I have an ATI Radeon 7500 video card.  I'm using whatever Ubuntu installed by default.  I have no real issues with the exception that 3d acceleration is a little slow.  Would using the fglrx driver be of any help with this video card?

---

### Post by mlomker on 2005-10-13
> I have an ATI Radeon 7500 video card. 

It isn't supported.  8500+

---

### Post by darknuala on 2005-10-13
Thanks!  I guess that was my problem when I tried using that whenever I tried to install gentoo a while back.  I switched to ubuntu, because i didn't have any issues with the video showing.

Thanks, again!

---

### Post by jiahanhao on 2005-10-13
[QUOTE=mlomker]I'm also curious why you didn't use 8.16.20?  I'm not aware of any serious problems.  The new 8.18.6 driver primarily fixes the dri (monitor resolution detection) problem for certain monitors and doesn't offer better performance or features.[/QUOTE]

It seemed that there was no support for the mobility x800 under the 8.16 driver, so I was hoping the 8.18 would include it. Does anyone know if there is a fixed libdri for 64 bit distros?

---

### Post by mlomker on 2005-10-13
>  8.18 would include it. Does anyone know if there is a fixed libdri for 64 bit distros?

It isn't [officially supported]("https://a248.e.akamai.net/f/674/9448/0/www2.ati.com/drivers/linux/linux_8.18.6.html#172478") under 8.18.6, either.  The difference is that the 8.16.20 drivers are tested and work under Breezy, whereas I haven't gotten the new ones to run in 3D yet.  2D is working for me.

---

### Post by jiahanhao on 2005-10-13
[QUOTE=mlomker]It isn't [officially supported]("https://a248.e.akamai.net/f/674/9448/0/www2.ati.com/drivers/linux/linux_8.18.6.html#172478") under 8.18.6, either.  The difference is that the 8.16.20 drivers are tested and work under Breezy, whereas I haven't gotten the new ones to run in 3D yet.  2D is working for me.[/QUOTE]

Ahh, I tried using the chipid for the mobility x800 xt in the 8.16.20 driver, and it seems it works under there, but I'm still having the DRI problem.

---

### Post by jecos on 2005-10-13
Ati installer should work fine if you make sure fglrx-control, fglrx-driver and linux-restricted modules are completely removed... search fglrx in synaptic and it will show those three to remove completely..

---

### Post by born_confused on 2005-10-13
sorry, linux-restricted-modules?

hoary ran fine with that, Im sure. I use madwifi, so restricted is pretty much a must.

---

### Post by mlomker on 2005-10-13
> I use madwifi, so restricted is pretty much a must.

Then don't upgrade to the 8.18 driver.  There's no reason for most people to do so.

---

### Post by quazi on 2005-10-13
I'm guessing the Compositing Extension isn't enabled yet with these new drivers?

---

### Post by born_confused on 2005-10-13
[QUOTE=mlomker]Then don't upgrade to the 8.18 driver.  There's no reason for most people to do so.[/QUOTE]

Hmm, Ive been told by several users that theres a performance enhancement. What I dont understand is the issue with restricted-modules, if the previous driver had no problem, why this one? Is it specific to this one only, or will this continue?

---

### Post by mlomker on 2005-10-13
> What I dont understand is the issue with restricted-modules, if the previous driver had no problem, why this one? Is it specific to this one only, or will this continue?

They're handling the restricted modules differently now.  Basically they get copied to the tmpfs filesystem and overwrite any driver that you try to manually install.

ATI's own website says that the only change is dri fixes.  If somebody managed to get it installed on Ubuntu then I really want to hear about it, though.  I can't get rid of Mesa no matter what I try.  My problem might be amd64 specific, though.  I don't have an x86 box to try it on.

---

### Post by born_confused on 2005-10-13
[QUOTE=mlomker]They're handling the restricted modules differently now.  Basically they get copied to the tmpfs filesystem and overwrite any driver that you try to manually install.

ATI's own website says that there's no performance difference.  If somebody managed to get it installed on Ubuntu then I really want to hear about it, though.  I can't get rid of Mesa no matter what I try.  My problem might be amd64 specific, though.  I don't have an x86 box to try it on.[/QUOTE]

ahh ok thank you. I dont know if those who mentioned peformance are ubuntu users. Reading that I doubt it. It seems every new driver must get into restricted-modules.

---

### Post by daniels on 2005-10-13
it has nothing to do with that.  it's failing to load the kernel module, not complaining about a dri version mismatch.  'sudo modprobe fglrx' on the command line will help enlighten you, probably.

---

### Post by born_confused on 2005-10-13
[QUOTE=daniels]it has nothing to do with that.  it's failing to load the kernel module, not complaining about a dri version mismatch.  'sudo modprobe fglrx' on the command line will help enlighten you, probably.[/QUOTE]

well, when I tried it earlier, the module loaded. However it then wasnt used. By that I mean no error reported directly, it did mention something about kernel context in `dmesg` and `lsmod` showed fglrx. However, you know this better than I do for sure.

---

### Post by jiahanhao on 2005-10-14
# LIBGL_DEBUG=verbose glxinfo

tells me that the DRI module complains that the card does not support direct rendering... guess I'll be waiting for ATI to release a driver that supports the mobility x800

---

### Post by jiahanhao on 2005-10-17
I just want to say: Screw you ATI, for not releasing a driver that supports my video card and making me wait another two months to hope and pray that I will have working video acceleration...

---

### Post by Septor on 2005-10-17
[QUOTE=jiahanhao]# LIBGL_DEBUG=verbose glxinfo

tells me that the DRI module complains that the card does not support direct rendering... guess I'll be waiting for ATI to release a driver that supports the mobility x800[/QUOTE]

Have you tried checking your Xorg.0.log to see if they problem is your set up, not the lack of support for your video card?

---

### Post by Golgoth on 2005-10-17
[QUOTE=darknuala]I have an ATI Radeon 7500 video card.  I'm using whatever Ubuntu installed by default.  I have no real issues with the exception that 3d acceleration is a little slow.  Would using the fglrx driver be of any help with this video card?[/QUOTE]

try the "radeon" driver.
it's free and supports 3D acceleration for your card.
it work fine on my 7500...

some info [here]("http://ubuntuforums.org/showpost.php?p=413031&postcount=10")

---

### Post by superm1 on 2005-10-17
[QUOTE=mlomker]Then don't upgrade to the 8.18 driver.  There's no reason for most people to do so.[/QUOTE]

Well i'm particularly looking forward to this being in the restricted-modules.  
Check out rage3d forums, and you'll see that this driver introduces power management for the ATI chips in laptops.  I have stuck with the radeon driver and given up opengl apps on my laptop so that I could use DynamicClocks.

Is there any way then to use madwifi provided by ubuntu packaging and to use this ATI driver, or will I just have to blow restricted modules, build madwifi myself and use the ATI installer?

edit
Here is the link
[http://www.rage3d.com/board/showpost.php?p=1333961451&postcount=1](http://www.rage3d.com/board/showpost.php?p=1333961451&postcount=1)

---

