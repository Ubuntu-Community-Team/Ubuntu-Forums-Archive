---
title: "No xserver with ATI RADEON XPRESS 200"
date: 2006-03-08
forum: Multimedia &amp; Video
---

### Post by bardu on 2006-03-08
Hi all,

it seems to be a common problem with the ATI RADEON XPRESS 200. I have a HP AMD Athlon 64 and don't get the xserver. I downloaded the newest driver and get this if I run the installer:
```
 
sudo sh ./ati-driver-installer-8.22.5-x86_64.run --buildpkg Ubuntu/breezy
Password:
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.22.5......................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
./packages/Ubuntu/ati-packager.sh: line 51: dpkg-architecture: command not foundError: unsupported architecture:
Removing temporary directory: fglrx-install

```

Can someone please give me advice.

Thanks,
Stephan

---

### Post by bardu on 2006-03-08
Sorry my mistake, should better read the guide.

Anyways, I went through all the steps and still have no xserver.

```
fglrxinfo
``` tell me:  unable to open display : 0.

I would really appreciate any useful help.

Stephan

---

### Post by bardu on 2006-03-08
No use, I tried again but same thing. /var/log/Xorg.0.log say fatal server error, but have no idea what the error caused.
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 root@crested.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF] 
Current Operating System: Linux ubuntu2 2.6.12-10-amd64-generic #1 Mon Feb 13 12:14:05 UTC 2006 x86_64
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:14:05 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar  8 13:16:07 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig Screen 0" (0)
(**) |   |-->Monitor "aticonfig Monitor 0"
(**) |   |-->Device "ATI Graphics Adapter 0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) PCI: 00:00:0: chip 1002,5950 card 103c,2a26 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4379 card 103c,2a26 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 103c,2a26 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 103c,2a26 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 103c,2a26 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,2a26 rev 11 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,2a26 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 103c,2a26 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,2a27 rev 02 class 04,01,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5954 card 103c,2a26 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:03:0: chip 10ec,8139 card 103c,2a26 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:05:0: chip 1106,3044 card 0003,000f rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:0), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc unknown chipset (0x5954) rev 0, Mem @ 0xd8000000/27, 0xfdef0000/16, I/O @ 0xee00/8
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
	[0] -1	0	0xfddfe000 - 0xfddfe7ff (0x800) MX[B]
	[1] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[8] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[13] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[14] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[16] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[17] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[19] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfddfe000 - 0xfddfe7ff (0x800) MX[B]
	[1] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[8] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[13] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[14] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[16] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[17] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[19] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
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
	[5] -1	0	0xfddfe000 - 0xfddfe7ff (0x800) MX[B]
	[6] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[13] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[19] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[20] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[21] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[23] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[26] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
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
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
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
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

Fatal server error:
Module load failure


Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


```

---

### Post by brucehohl on 2006-03-20
I think you may be missing some of the dependencies needed by the ATI installer.  See the post below for packages to install before running the installer.  If the kernel-headers package is not installed as a dependency of the packages in the post below, than install that package as well.

See this post:  [http://www.ubuntuforums.org/showthread.php?t=144053&highlight=xpress+200](http://www.ubuntuforums.org/showthread.php?t=144053&highlight=xpress+200)

Cheers,
Bruce

---

