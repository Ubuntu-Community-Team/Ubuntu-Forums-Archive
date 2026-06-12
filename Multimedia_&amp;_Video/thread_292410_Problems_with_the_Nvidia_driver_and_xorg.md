---
title: "Problems with the Nvidia driver and xorg"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by NorthernSoul on 2006-11-03
For some reason after installing the Nvidia driver supplied in the extra repositories xorg kicks up some errors (Look below for the Log). I installed it the regular way using these commands:
```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
```
The enable command comes back fine, telling me that I need to restart X before it can use the driver. When I do it, a blinking cursor on a black screen comes back, and stays there until the whole OS restarts. When that happens it comes up with these errors:
(I know it's long, but I didn't want to cut anything out, since I don't know what's important and what isn't)

```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux kevin-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  3 17:06:20 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
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
(II) PCI: 00:00:0: chip 1002,5950 card 1462,7145 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:11:0: chip 1002,437a card 1462,7141 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:12:0: chip 1002,4379 card 1462,7141 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 1462,7145 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1462,7145 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1462,7145 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 1462,7145 rev 10 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 1462,7145 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 1462,7145 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 1462,b000 rev 01 class 04,01,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0141 card 3842,c369 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:03:0: chip 10ec,8139 card 1462,145c rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1106,3044 card 1462,145d rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xfbffffff (0x8000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce 6600] rev 162, Mem @ 0xf4000000/26, 0xd0000000/28, 0xfa000000/24
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
(II) PCI I/O resource overlap reduced 0x00004100 from 0x0000411f to 0x000040ff
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xffffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[2] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[3] -1	0	0xfe02a000 - 0xfe02a3ff (0x400) MX[B]
	[4] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e1ff (0x200) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[14] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[15] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[16] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[17] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[18] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[19] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[20] -1	0	0x0000f800 - 0x0000f803 (0x4) IX[B]
	[21] -1	0	0x0000f900 - 0x0000f907 (0x8) IX[B]
	[22] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[23] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[25] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[2] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[3] -1	0	0xfe02a000 - 0xfe02a3ff (0x400) MX[B]
	[4] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e1ff (0x200) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[14] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[15] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[16] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[17] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[18] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[19] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[20] -1	0	0x0000f800 - 0x0000f803 (0x4) IX[B]
	[21] -1	0	0x0000f900 - 0x0000f907 (0x8) IX[B]
	[22] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[23] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[25] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
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
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02a3ff (0x400) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e1ff (0x200) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000de00 - 0x0000de7f (0x80) IX[B]
	[20] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[21] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[22] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[23] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[24] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[25] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[26] -1	0	0x0000f800 - 0x0000f803 (0x4) IX[B]
	[27] -1	0	0x0000f900 - 0x0000f907 (0x8) IX[B]
	[28] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[29] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[30] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[31] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[32] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[33] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
	compiled for 4.0.2, module version = 1.0.8774
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
	compiled for 4.0.2, module version = 1.0.8774
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
(II) NVIDIA X Driver  1.0-8774  Tue Aug  1 20:56:50 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found
```

BTW, my graphics card is an Nvidia 6600 PCI-Express model, if it helps. Any help would be appreciated.

---

### Post by NorthernSoul on 2006-11-06
Anyone? Unfortunately, if I can't get this to work I'll end up going back to Windows.

---

### Post by amd-64 on 2006-11-15
A few of the things you could try

1. Remove all wacom packages, unless you are using a wacom graphics tablet
```

sudo apt-get remove xserver-xorg-input-wacom wacom-tools 
```

2. Backup your /etc/X11/xorg.conf and create a new file using 
```
 sudo dpkg-reconfigure xserver-xorg
```

3. Post your old and new xorg.conf files.

4. Try the nv driver instead of nvidia (check the forums for more help on this)

5. Comment out the BusID PCI:.... line in xorg.conf (you could try this first and see if autodetection works)

Good luck

---

