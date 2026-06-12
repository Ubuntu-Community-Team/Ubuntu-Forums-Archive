---
title: "Nvidia GeForce FX 5500 &amp; 23&quot; Apple Cinema Display"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by jzwill on 2007-04-13
OK, I have been banging my head on this now (googling, hacking, etc) for about 8 hrs now. I think it is time I made my 1st post to the forum.  First off, I am an relatively new Ubuntu user (aren't we all?) but a somewhat seasoned Linux user.

I have a GeForce FX 5500 video card.  The card has one VGA port and one DVI port.  I have an old Dell CRT monitor that works just fine connected to the VGA port.  I would like to plug in my Apple 23 " HD Cinema Display to the DVI port.  I have installed the nvidia driver, searched this and other forums for help on this.  I have gotten to a point where atleast X will start and I can see what I am doing on the CRT monitor, but the Apple display remains blank.  (Note:I get the same basic errs when I try to configure the one display - the Apple - by itself. I just don't have a way to see what is going on, graphically when I do this, so I am configuring both)

Here is my Xorg.0.log (Notice the "Mode ... to large for Apple..." lines:
```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux ubuntu64 2.6.17-11-generic #2 SMP Tue Mar 13 22:06:20 UTC 2007 x86_64
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 13 18:36:48 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Crt" (0)
(**) |   |-->Monitor "CRT"
(**) |   |-->Device "NVIDIA GeForce 5500 B"
(**) |-->Screen "Cinema" (1)
(**) |   |-->Monitor "Apple Cinema Display"
(**) |   |-->Device "NVIDIA GeForce 5500"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "on"
(**) Xinerama: enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 1043,813f rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1043,813f rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1043,813f rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1043,813f rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1043,80a7 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1043,813f rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1043,813f rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0326 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 1282,9102 card 4554,434e rev 31 class 02,00,00 hdr 00
(II) PCI: 02:08:0: chip 4444,0016 card 0070,8801 rev 01 class 04,00,00 hdr 00
(II) PCI: 02:0a:0: chip 1102,0004 card 1102,2001 rev 04 class 04,01,00 hdr 80
(II) PCI: 02:0a:1: chip 1102,7003 card 1102,0040 rev 04 class 09,80,00 hdr 80
(II) PCI: 02:0a:2: chip 1102,4001 card 1102,0010 rev 04 class 0c,00,10 hdr 80
(II) PCI: 02:0b:0: chip 1106,3044 card 1043,808a rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc4800000 - 0xe47fffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe4800000 - 0xec7fffff (0x8000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xfd000000/24, 0xd0000000/28, BIOS @ 0xfe9e0000/17
(--) PCI: (2:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xe8000000/26
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[3] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[10] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[14] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[19] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[20] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[21] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[22] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[26] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[27] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[3] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[10] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[14] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[19] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[20] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[21] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[22] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[26] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[27] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
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
	[4] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[11] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[14] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[31] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[32] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[33] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) LoadModule: "ic2"
(WW) Warning, couldn't open module ic2
(II) UnloadModule: "ic2"
(EE) Failed to load module "ic2" (module does not exist, 0)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:56:44 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[11] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[14] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[31] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[32] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[33] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[11] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[14] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[34] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[35] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[36] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     Dell  M991 (CRT-0)
(--) NVIDIA(0):     Apple Cinema HD (DFP-0)
(--) NVIDIA(0): Dell  M991 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Apple Cinema HD (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): Apple Cinema HD (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1152x768"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1152 x 768
(--) NVIDIA(0): DPI set to (72, 72); computed from "UseEdidDpi" X config option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0
(--) NVIDIA(1): VideoRAM: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 04.34.20.69.01
(II) NVIDIA(1): Detected AGP rate: 8X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(1):     Dell  M991 (CRT-0)
(--) NVIDIA(1):     Apple Cinema HD (DFP-0)
(--) NVIDIA(1): Dell  M991 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(1): Apple Cinema HD (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(1): Apple Cinema HD (DFP-0): Internal Single Link TMDS
(WW) NVIDIA(1): Mode "640x480" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "800x600" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1024x768" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1280x960" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1280x1024" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1600x1200" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1280x768" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1280x800" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1400x1050" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1440x900" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1600x1024" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "640x480" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "800x600" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1024x768" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1280x960" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1280x1024" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(WW) NVIDIA(1): Mode "1600x1200" is too large for Apple Cinema HD (DFP-0);
(WW) NVIDIA(1):     discarding.
(II) NVIDIA(1): Assigned Display Device: DFP-0
(WW) NVIDIA(1): No valid modes for "1920x1200"; removing.
(WW) NVIDIA(1): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(1): No valid modes for "1280x960"; removing.
(WW) NVIDIA(1): No valid modes for "1024x768"; removing.
(WW) NVIDIA(1): No valid modes for "800x600"; removing.
(WW) NVIDIA(1): No valid modes for "640x480"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 800 x 600
(--) NVIDIA(1): DPI set to (99, 98); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[7] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[8] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[9] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[10] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[11] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[12] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[13] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[14] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[15] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[16] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[25] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[28] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[29] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[36] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[37] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[38] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1152x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
SetGrabKeysState - disabled
```

And here is my xorg.conf file:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Oct 16 22:13:48 PDT 2006

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
    Screen      0  "Crt" LeftOf "Cinema"
    Screen	1  "Cinema"
    Option 	"Xinerama" "on"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "ic2"
    Load           "bitmap"
    Load           "ddc"
#    Load	"dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Apple Cinema Display"
    Option          "DPMS"
    HorizSync      28-96 
    VertRefresh    43-60 
    Modeline "1920x1200" 155.0 1920 1984 2016 2144 1200 1203 1206 1212 -HSync +Vsync
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option	"DPMS"
	HorizSync 30-80
	VertRefresh 50-80
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 5500"
    Driver         "nvidia"
    BusID	"PCI:1:0:0"
EndSection

Section "Device"
	Identifier "NVIDIA GeForce 5500 B"
	Driver "nvidia"
	BusID "PCI:1:0:0"
	Screen	1
EndSection
	
Section "Screen"
    Identifier     "Cinema"
    Device         "NVIDIA GeForce 5500"
    Monitor        "Apple Cinema Display"
    DefaultDepth    24
    SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
    SubSection     "Display"
        Depth	24 
        Modes  "1920x1200" "1680x1050" "1280x960" "1024x768" "800x600" "640x480" 
    EndSubSection
EndSection

Section "Screen"
	Identifier "Crt"
	Device "NVIDIA GeForce 5500 B"
	Monitor "CRT"
	DefaultDepth 24
	SubSection "Display"
		Depth		1
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	Subsection "Display"
		Depth 24
		Modes "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection	

```

---

### Post by rpresser on 2007-04-18
For what it's worth, I am experiencing exactly the same problem -- except with a PC using Windows XP. (Please control your gag reflex.) This leads me to believe it may be a hardware incompatibility of some sort.

Yesterday I had the ACD hooked up as one of three monitors on my first XP system.  It was connected to a nVidia GeForce4 MX 440.  It seemed to be working fine. Bright, crisp, responsive.

Today I have it hooked up to a different PC with the same card, and the monitor remains blank.  XP thinks its there; I can shift windows onto that portion of the desktop and back without problem. Today, bupkis.

---

