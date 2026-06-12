---
title: "Sager 8790 ATI rv350 mobility 9600 pro"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by dtruesdale on 2006-10-07
Bad story, I have had this working under gentoo so I know it works. I am just trying to figure out where under Ubuntu it has gone wrong. I love Ubuntu but things like this are a hassle. Here is the Xorg.log:

[HTML]X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux sager 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct  7 11:46:28 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1558,0800 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1558,0800 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1558,0800 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1558,0800 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1558,0800 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1558,0800 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1558,0800 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1558,0800 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1558,0800 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24d6 card 1558,0800 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4e50 card 1558,0870 rev 00 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 104c,ac50 card 4800,0000 rev 02 class 06,07,00 hdr 02
(II) PCI: 03:01:0: chip 104c,8026 card 1558,0500 rev 00 class 0c,00,10 hdr 00
(II) PCI: 03:02:0: chip 105a,0d30 card 1558,0800 rev 02 class 01,80,00 hdr 00
(II) PCI: 03:03:0: chip 10ec,8169 card 1558,0800 rev 10 class 02,00,00 hdr 00
(II) PCI: 03:04:0: chip 168c,0013 card 1458,e911 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd0100000 - 0xd01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,7), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd0200000 - 0xd02fffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x52ffffff (0x3000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:0:0), (3,4,7), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[1] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x51ffffff (0x2000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] rev 0, Mem @ 0xe0000000/28, 0xd0100000/16, I/O @ 0x3000/8
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
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdfffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[1] -1	0	0xd0214800 - 0xd02148ff (0x100) MX[B]
	[2] -1	0	0x52000000 - 0x5200ffff (0x10000) MX[B]
	[3] -1	0	0xd0220000 - 0xd023ffff (0x20000) MX[B]
	[4] -1	0	0xd0210000 - 0xd0213fff (0x4000) MX[B]
	[5] -1	0	0xd0214000 - 0xd02147ff (0x800) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x53000000 - 0x530003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[14] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[15] -1	0	0x00004440 - 0x00004443 (0x4) IX[B]
	[16] -1	0	0x00004448 - 0x0000444f (0x8) IX[B]
	[17] -1	0	0x00004444 - 0x00004447 (0x4) IX[B]
	[18] -1	0	0x00004450 - 0x00004457 (0x8) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[20] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[21] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[23] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[24] -1	0	0x00002060 - 0x0000206f (0x10) IX[B]
	[25] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[26] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[27] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[28] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[29] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[1] -1	0	0xd0214800 - 0xd02148ff (0x100) MX[B]
	[2] -1	0	0x52000000 - 0x5200ffff (0x10000) MX[B]
	[3] -1	0	0xd0220000 - 0xd023ffff (0x20000) MX[B]
	[4] -1	0	0xd0210000 - 0xd0213fff (0x4000) MX[B]
	[5] -1	0	0xd0214000 - 0xd02147ff (0x800) MX[B]
	[6] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[7] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[8] -1	0	0x53000000 - 0x530003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[10] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[11] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[14] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[15] -1	0	0x00004440 - 0x00004443 (0x4) IX[B]
	[16] -1	0	0x00004448 - 0x0000444f (0x8) IX[B]
	[17] -1	0	0x00004444 - 0x00004447 (0x4) IX[B]
	[18] -1	0	0x00004450 - 0x00004457 (0x8) IX[B]
	[19] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[20] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[21] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[22] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[23] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[24] -1	0	0x00002060 - 0x0000206f (0x10) IX[B]
	[25] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[26] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[27] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[28] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[29] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
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
	[4] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[5] -1	0	0xd0214800 - 0xd02148ff (0x100) MX[B]
	[6] -1	0	0x52000000 - 0x5200ffff (0x10000) MX[B]
	[7] -1	0	0xd0220000 - 0xd023ffff (0x20000) MX[B]
	[8] -1	0	0xd0210000 - 0xd0213fff (0x4000) MX[B]
	[9] -1	0	0xd0214000 - 0xd02147ff (0x800) MX[B]
	[10] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[11] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[12] -1	0	0x53000000 - 0x530003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[14] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[15] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[20] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[21] -1	0	0x00004440 - 0x00004443 (0x4) IX[B]
	[22] -1	0	0x00004448 - 0x0000444f (0x8) IX[B]
	[23] -1	0	0x00004444 - 0x00004447 (0x4) IX[B]
	[24] -1	0	0x00004450 - 0x00004457 (0x8) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[26] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[27] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[28] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[29] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[30] -1	0	0x00002060 - 0x0000206f (0x10) IX[B]
	[31] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[32] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[33] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[34] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[35] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
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
	compiled for 6.8.99.8, module version = 8.29.6
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
	compiled for 6.99.99.904, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) ATI Radeon/FireGL: The following chipsets are supported:
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
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300/X550 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 SE (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600/X550 Series (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), FireMV 2400 (RV380 3151),
	MOBILITY RADEON X300 (M22 3152), MOBILITY FireGL V3200 (M24 3154),
	RADEON X800 (R420 4A48), RADEON X800 PRO (R420 4A49),
	RADEON X800 SE (R420 4A4A), RADEON X800 XT (R420 4A4B),
	RADEON X800 (R420 4A4C), FireGL X3-256 (R420 4A4D),
	MOBILITY RADEON 9800 (M18 4A4E), RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 GTO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), FireGL V7200 (R480 5D50),
	RADEON X850 XT (R480 5D52), RADEON X850 (R481 4B48),
	RADEON X850 XT (R481 4B49), RADEON X850 SE (R481 4B4A),
	RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700/X550 Series (RV410 5E4F),
	MOBILITY RADEON X700 (M26 5652), MOBILITY RADEON X700 (M26 5653),
	MOBILITY RADEON X700 XL (M26-XC 564F),
	RADEON 9000/9100 IGP Series (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000 IGP (RL300MB 7835),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 XT (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 Series (R520 7108),
	RADEON X1800 Series (R520 7109), RADEON X1800 Series (R520 710A),
	RADEON X1800 Series (R520 710B), RADEON X1800 Series (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	RADEON X1300 PRO (RV505 7143), RADEON X1300 (RV505 7147),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1300 Series (RV505 715F), RADEON X1600 Series (RV515 7140),
	RADEON X1300 Series (RV515 7142), MOBILITY FireGL (M54 GL 7144),
	MOBILITY RADEON X1400 (M54 7145), RADEON X1300 Series (RV515 7146),
	MOBILITY RADEON X1300 (M52 7149), MOBILITY RADEON X1300 (M52 714A),
	RADEON X1300 Series (RV515 714D), RADEON X1300 Series (RV515 714E),
	FireGL V3300 (RV515 7152), RADEON X1300 Series (RV515 715E),
	RADEON X1300 (RV516 7180), RADEON X1600 Series (RV516 7181),
	RADEON X1300 (RV516 7183), MOBILITY RADEON X1450 (M64P 7186),
	RADEON X1300 (RV516 7187), MOBILITY RADEON X1350 (M62P 718B),
	MOBILITY RADEON X1350 (M62CSP 718C),
	MOBILITY RADEON X1450 (M64CSP 718D),
	MOBILITY RADEON X1350 (M62S 7196), RADEON X1900 (R580 7240),
	RADEON X1900 (R580 7243), RADEON X1900 (R580 7244),
	RADEON X1900 (R580 7245), RADEON X1900 (R580 7246),
	RADEON X1900 (R580 7247), RADEON X1900 (R580 7248),
	RADEON X1900 (R580 7249), RADEON X1900 (R580 724A),
	RADEON X1900 (R580 724B), RADEON X1900 (R580 724C),
	RADEON X1900 (R580 724D), FireStream 2U (R580 724E),
	FireStream 2U (R580 724F), RADEON X1600 Series (RV530 71C0),
	RADEON X1600 Series (RV530 71C2), MOBILITY FireGL V5200 (M56 71C4),
	MOBILITY RADEON X1600 (M56 71C5),
	RADEON X1600 Series (RV530 LE 71C6),
	RADEON X1600 Series (RV530 VE 71CE), FireGL V3400 (RV530 71D2),
	MOBILITY RADEON X1700 (M66-XT 71D6), FireGL V5200 (RV530 71DA),
	RADEON X1600 Series (RV530 SE 71DE), RADEON X1600 XT (RV535 XT 71C1),
	MOBILITY FireGL V5250 (M66GL 71D4),
	MOBILITY RADEON X1700 (M66-P 71D5), FireGL V7400 (RV570 GL 728C),
	RADEON Xpress 1200 (RS600 7941), RADEON Xpress 1200 (RS600 7942)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.29.6
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.29g1                           
(II) ATI Proprietary Linux Driver Build Date: Sep 19 2006 16:28:05
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.29.1.1.2.3-driver-lnx-x86-x86_64-294118
(--) Assigning device section with no busID to primary device
(--) Chipset MOBILITY RADEON 9600/9700 (M10/M11 4E50) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[5] -1	0	0xd0214800 - 0xd02148ff (0x100) MX[B]
	[6] -1	0	0x52000000 - 0x5200ffff (0x10000) MX[B]
	[7] -1	0	0xd0220000 - 0xd023ffff (0x20000) MX[B]
	[8] -1	0	0xd0210000 - 0xd0213fff (0x4000) MX[B]
	[9] -1	0	0xd0214000 - 0xd02147ff (0x800) MX[B]
	[10] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[11] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[12] -1	0	0x53000000 - 0x530003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[14] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[15] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[20] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[21] -1	0	0x00004440 - 0x00004443 (0x4) IX[B]
	[22] -1	0	0x00004448 - 0x0000444f (0x8) IX[B]
	[23] -1	0	0x00004444 - 0x00004447 (0x4) IX[B]
	[24] -1	0	0x00004450 - 0x00004457 (0x8) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[26] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[27] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[28] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[29] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[30] -1	0	0x00002060 - 0x0000206f (0x10) IX[B]
	[31] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[32] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[33] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[34] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[35] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81dbbd0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd0200000 - 0xd020ffff (0x10000) MX[B]
	[5] -1	0	0xd0214800 - 0xd02148ff (0x100) MX[B]
	[6] -1	0	0x52000000 - 0x5200ffff (0x10000) MX[B]
	[7] -1	0	0xd0220000 - 0xd023ffff (0x20000) MX[B]
	[8] -1	0	0xd0210000 - 0xd0213fff (0x4000) MX[B]
	[9] -1	0	0xd0214000 - 0xd02147ff (0x800) MX[B]
	[10] -1	0	0xd0000800 - 0xd00008ff (0x100) MX[B]
	[11] -1	0	0xd0000c00 - 0xd0000dff (0x200) MX[B]
	[12] -1	0	0x53000000 - 0x530003ff (0x400) MX[B]
	[13] -1	0	0xd0000000 - 0xd00003ff (0x400) MX[B]
	[14] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[15] -1	0	0xd0100000 - 0xd010ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[23] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[24] -1	0	0x00004440 - 0x00004443 (0x4) IX[B]
	[25] -1	0	0x00004448 - 0x0000444f (0x8) IX[B]
	[26] -1	0	0x00004444 - 0x00004447 (0x4) IX[B]
	[27] -1	0	0x00004450 - 0x00004457 (0x8) IX[B]
	[28] -1	0	0x00001c00 - 0x00001c7f (0x80) IX[B]
	[29] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[30] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[31] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[32] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[33] -1	0	0x00002060 - 0x0000206f (0x10) IX[B]
	[34] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[35] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[36] -1	0	0x00001ce0 - 0x00001cff (0x20) IX[B]
	[37] -1	0	0x00001cc0 - 0x00001cdf (0x20) IX[B]
	[38] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[39] 0	0	0xd01203b0 - 0xd01203bb (0xc) IS[B]
	[40] 0	0	0xd01203c0 - 0xd01203df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "MOBILITY RADEON 9600/9700 (M10/M11 4E50)" (Chipset = 0x4e50)
(--) fglrx(0): (PciSubVendor = 0x1558, PciSubDevice = 0x0870)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xd0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 262080 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON 9600   
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: P11 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.29.6
	ABI class: X.Org Server Extension, version 0.2
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MS_  Model: 0  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 121.5 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1680  h_sync: 1736  h_sync_end 1768 h_blank_end 1872 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1051  v_sync_end 1052 v_blanking: 1062 v_border: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(EE) fglrx(0): PreInitDAL failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "ddc"
(II) UnloadModule: "fglrxdrm"
(II) Unloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) UnloadModule: "drm"
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Now here is the xorg.conf file:

Yes the driver at the moment is ati since fglrx does what is above.


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
#Section "Monitor"
#	Identifier   "aticonfig-Monitor[0]"
#	HorizSync    28.0 - 51.0
#	VertRefresh  43.0 - 60.0
#	Option	    "DPMS"
#EndSection
#Section "Device"
#	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
#	Driver      "ati"
#	BusID       "PCI:1:0:0"
#EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Modeline    "1680x1050" 119.12 1680 1728 1760 1840 1050 1052 1058 1080
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
[/HTML]
Any ideas or hints to this?

The laptop is the Sager 8790 with p4 3.4ghz 1gb ram rv350 M11 radeon mobility 9600 pro with 256mb the kernel is the 2.6.15-27. It has a LCD that is set to 1680x1050. Thanks in advance.

---

### Post by RudolfMDLT on 2006-10-07
Hi!,

a bit more detail would be nice! Did you download the restricted drivers? Ubuntu is not shipped with them. If yes then:

Under the device section change "ati" to "fglrx"

post back with results.

---

### Post by dtruesdale on 2006-10-07
Yes I have run the fglrx driver it freezes just as it loads the screen for the login all I have is the bar and Kubuntu on the sceen. The results you see are from the fglrx driver not the ati. The ati is in the xorg.conf due to that is what I had to use to get back into X.

---

### Post by RudolfMDLT on 2006-10-07
Okay...

Ati is a real pain to get working in Ubuntu and i believe in linux in general.

lets just try a smaller resolution for now? The fact that the login screen is displayed meens that the driver is working and hanging as soon as KDE starts loading and starts requiring it to render it bombs out.

Secondly, after the smaller res, your xorg.conf is a mess! you have been editing that thing like mad! :)  

If the resolution reduction doesn't work then restart the machine and in grub, choose recovery mode. log in as root or if you don't want to, use "sudo" infront of every command.

enter the following code:

aticonfig --initial

aticonfig --overlay-type=Xv

Shutdown -r 0 now

Please remeber sudo in front of every command if you don't log in as root.

---

### Post by dtruesdale on 2006-10-07
Ok took it back to fresh install state and re0installed the driver and still when using fglrx all I get is the kubuntu logo with the bar and there it sets, nevedr goes to the login. It keeps saying in the xorg.log at the end fatal sever error: no screen found.

---

### Post by RudolfMDLT on 2006-10-08
Sorry for only replying now. I live on the other side of the world.

Please post your xorg.conf. I think the driver and the display/screen sections are not pionting to the right driver. If your xorg.conf is still screwy, you can find my xorg.conf here:

[http://ubuntuforums.org/showthread.php?p=1593019#post1593019](http://ubuntuforums.org/showthread.php?p=1593019#post1593019)

4th last post.

I think youre gonna wake up when I'm gonna be studying so here is some home work for you to do: :)

1) Make a backup of your xorg.conf. Copy and past mine, changing where ever you see "ATI Technologies, Inc. RV350 AP [Radeon 9600]" to 

ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"

and copy and paste your monitor config over mine. Leave my resolution setting for now. Restart the machine and see what happens.

If this does not work, get to a console, log in,  and type in:

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv

sudo shutdown -r 0 now

Then if that doesn't work follow option number 2)
                 
                          ***
2)
The following will tell you to install some packadges. You have to have the restricted modules enabled. If you haven't done this find a post on the forum that tells you how to enable the restricted repositories, there are plenty of them. Then only... 

Go into Synaptic and find these packadges. Right click on the packadges and say uninstall but DO NOT click the option of permanently deleting them.

Then print or write down the following. Restart you machine. When GRUB loads, select recovery mode.

You will be booted into a console. Login in using root as the user name and your root password. If you log in as root you don't need to use sudo.

Copy the following into the console

sudo apt-get update


sudo apt-get install linux-restricted-modules-$(uname -r) 

Install all of the restricted kernel modules. The restricted
module of concern here is called fglrx.
The way that linux does drivers is by removable "modules" that
load into the kernel. At any time, you can pull up a Terminal
and type "lsmod" to see all the loaded modules. Fglrx is the
ATI propietary driver that loads into the kernel.

Code:

sudo apt-get install xorg-driver-fglrx

This installs all of the opengl & x11 related items for the driver
as well as any binaries that ATI distributes with the driver.

This package is seperate from the linux-restricted-modules package
because if a kernel update comes out, then you don't need to reinstall
all of the opengl,x11, and ati binaries. Instead, the only thing
that would change is the kernel module which comes in linux-restricted-modules.

Code:

sudo depmod -a


This updates the list of available kernel modules to reflect
fglrx being added. It can actually be done before installing
xorg-driver-fglrx.

Code:

sudo aticonfig --initial

This reads in your initial /etc/X11/xorg.conf. It then parses
it and updates it to change anything required for fglrx.
aticonfig actually has lots of other options that you can set
up as well including but not limited to multiple displays and power
management. If your curious run aticonfig --help to see.

Code:

sudo aticonfig --overlay-type=Xv

This enables the video overlay to be handled by Xv.
Video overlays can be handled either by Xv, X11, or opengl.
X11 is the straight X11 windowing protocol. If you use this,
most higher resolution videos will play pretty horribly.
Xv stands for XVideo. It is the defacto standard for video
playback, so if your driver supports it, you should use it.
Opengl plays back your video in an opengl texture. This can
be good in some cases, but you would have to experiment with it a bit. 



After all this enter the code:

shutdown -r 0 now


and restart the computer and see if it helps.

on my 3rd install, working out of gnome did not work, but working in a totall text enviroment kept Xorg from loading and solved my issue.

Goodluck.

---

### Post by dtruesdale on 2006-10-08
Ok last night I cleaned it up a bit and tried to re-install and got same results. here is the xorg.conf file:



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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "ati"
	BusID	    "PCI:1:0:0"
	Option	    "UseInternalAGPGART" "no"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"

EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

I will do what you posted and post back the results. I really hate this right now due to I want to use this unit for work (I have a programming job I have to do in over the next 6 weeks.) Thanks for your help on this.

---

### Post by dtruesdale on 2006-10-08
No joy and this is really bothering me, look at this from the bottom of the Xorg.0.log file:

II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.29.6
	ABI class: X.Org Server Extension, version 0.2
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS
(II) fglrx(0):  Display1: No EDID information from DDC.
(II) fglrx(0): Derived EDID from BIOS and internal tables for Display1:
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: MS_  Model: 0  Serial#: 0
(II) fglrx(0): Year: 1990  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 40  vert.: 30
(II) fglrx(0): Gamma: 1.00
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; Non RGB Multicolor Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
(II) fglrx(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 121.5 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1680  h_sync: 1736  h_sync_end 1768 h_blank_end 1872 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1051  v_sync_end 1052 v_blanking: 1062 v_border: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(EE) fglrx(0): PreInitDAL failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "ddc"
(II) UnloadModule: "fglrxdrm"
(II) Unloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) UnloadModule: "drm"
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

This appears to be where it is no matter what I do. This is a Sager 8790 Laptop with a 1680x1050 screen 17" widescreen. Is this the same issue as the HP laptops? Like I said I had this working great before under Gentoo.

---

### Post by dtruesdale on 2006-10-11
Problem solved and not in the way most would want, I installed Mepis 6.0 and it now works as it should. Sorry guys just tired of banging my head against a wall all day. The rest of my laptops remain Ubuntu/Kubuntu.

---

