---
title: "[SOLVED] radeonHD driver not working?"
date: 2008-05-15
forum: Multimedia Software
---

### Post by FoX_HunteR on 2008-05-15
after i re-built the xserver thingy and installed the driver and set it up to use it in the xorg.conf file, it seems to be ignoring it completely?

heres my xorg:
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver          "radeonhd"
EndSection

Section "Extensions"
	Option          "Composite" "Off"
EndSection

Section "ServerFlags"
	Option          "AIGLX" "Off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

i really dont know what else to do?
how do i get the drivers to actually work!

---

### Post by FoX_HunteR on 2008-05-16
can anyone help at all???
PLEASE, its my ONLY problem with linux, i dont want to have to throw it out just coz of 1 stupid problem!

---

### Post by phoenix12345 on 2008-05-16
> **FoX_HunteR said:**
> can anyone help at all???
PLEASE, its my ONLY problem with linux, i dont want to have to throw it out just coz of 1 stupid problem!

I've also compiled this driver for my card and X11 ignores it and switches back to VESA.

---

### Post by FoX_HunteR on 2008-05-16
yea, it wont even look sideways at it, for me it just goes on and proceeds to use no driver at all and everything lags, i NEED it to work as my card is PCIe and wont work with the standard drivers for some reason...

---

### Post by Yellow Pasque on 2008-05-16
Post your /var/log/Xorg.0.log

---

### Post by FoX_HunteR on 2008-05-17
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux da-beast-duo 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 17 21:54:42 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) Option "AIGLX" "Off"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1043,817a rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1043,8290 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1043,8179 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1043,8179 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 1043,8179 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1043,8179 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1043,2601 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1043,8179 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:01:0: chip 168c,0013 card 168c,1051 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 1969,2048 card 1043,8233 rev a0 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,94c3 card 1043,01c2 rev 00 class 03,00,00 hdr 80
(II) PCI: 04:00:1: chip 1002,aa10 card 1043,aa10 rev 00 class 04,03,00 hdr 80
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
(II) Bus 4: bridge is at (0:1:0), (0,4,4), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:0), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(4:0:0) ATI Technologies Inc unknown chipset (0x94c3) rev 0, Mem @ 0xe0000000/28, 0xdffe0000/16, I/O @ 0xe000/8, BIOS @ 0xdffc0000/17
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
	[0] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[1] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[2] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[3] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[4] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[5] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[6] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[9] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[10] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[11] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[12] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[20] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[21] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[22] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[1] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[2] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[3] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[4] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[5] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[6] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[9] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[10] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[11] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[12] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[20] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[21] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[22] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
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
	[4] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[5] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[6] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[7] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[8] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[9] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[10] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[26] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[27] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[28] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "radeonhd"
(II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.4.0.90, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
	RV505 : Radeon X1550, X1550 64bit.
	RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
	RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
	R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
	RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
	RV535 : Radeon X1300, X1650.
	RV550 : Radeon X2300 HD.
	RV560 : Radeon X1650.
	RV570 : Radeon X1950, X1950 GT; FireGL V7400.
	R580  : Radeon X1900, X1950; AMD Stream Processor.
	R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
	RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
	RV620 : Radeon HD 3450, HD 3470.
	RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
		FireGL V3600/V5600.
	RV635 : Radeon HD 3650, HD 3670.
	RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
	R680  : Radeon HD 3870 X2.
	M52   : Mobility Radeon X1300.
	M54   : Mobility Radeon X1400; M54-GL.
	M56   : Mobility Radeon X1600; Mobility FireGL V5200.
	M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
	M62   : Mobility Radeon X1350.
	M64   : Mobility Radeon X1450, X2300.
	M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
	M68   : Mobility Radeon X1900.
	M71   : Mobility Radeon HD 2300.
	M72   : Mobility Radeon HD 2400; Radeon E2400.
	M74   : Mobility Radeon HD 2400 XT.
	M76   : Mobility Radeon HD 2600;
		(Gemini ATI) Mobility Radeon HD 2600 XT.
	M82   : Mobility Radeon HD 3400.
	RS600 : Radeon Xpress 1200, Xpress 1250.
	RS690 : Radeon X1200, X1250, X1270.

(II) RADEONHD: version 1.2.1, built from git branch master, commit 867c8efa

(II) Primary Device is: PCI 04:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset RV610 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[5] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[6] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[7] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[8] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[9] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[10] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[26] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[27] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[28] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[5] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[6] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[7] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[8] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[9] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[10] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[26] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[27] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[28] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) RADEONHD(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Selected ShadowFB.
(II) RADEONHD(0): Unknown card detected: 0x94C3:0x1043:0x01C2.
	If - and only if - your card does not work or does not work optimally
	please contact radeonhd@opensuse.org to help rectify this.
	Use the subject: 0x94C3:0x1043:0x01C2: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an RV610 on an unidentified card
(II) RADEONHD(0): Mapped IO at 0xb7add000 (size 0x00010000)
(II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
(II) RADEONHD(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1043 SubsystemID: 0x01c2
	IOBaseAddress: 0xe000
	Filename: SV25680.BIN 
	BIOS Bootup Message: 

94C3.10.56.00.05.AS03                                                       


(II) RADEONHD(0): Analog TV Default Mode: 1
(II) RADEONHD(0): Found default TV Mode NTSC
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 16
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0xfffc000
(II) RADEONHD(0): AtomBIOS requests 16kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0xfffc000
(II) RADEONHD(0): Default Engine Clock: 525000
(II) RADEONHD(0): Default Memory Clock: 400000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.
(II) RADEONHD(0): PCI FB Address (BAR) is at 0x00000000 while card Internal Address is 0xE0000000
(II) RADEONHD(0): Mapped FB at (nil) (size 0x00000000)
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_TV, "7PIN_DIN TV1 CV", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACB, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_VGA, "VGA CRT1", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[2] {RHD_CONNECTOR_DVI, "DUAL_LINK_DVI_I DFP1 CRT2", RHD_DDC_1, RHD_HPD_0, { RHD_OUTPUT_LVTMA, RHD_OUTPUT_DACB } }
(--) RADEONHD(0): Attaching Output DAC B to Connector TV 7PIN_DIN
(--) RADEONHD(0): Attaching Output DAC A to Connector VGA 1
(--) RADEONHD(0): Attaching Output TMDS B to Connector DVI-I 1
(--) RADEONHD(0): Attaching Output DAC B to Connector DVI-I 1
(II) RADEONHD(0): RandR: Adding RRoutput TV_7PIN_DIN for Output DAC B
(II) RADEONHD(0): RandR: Adding RRoutput VGA_1 for Output DAC A
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/digital for Output TMDS B
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/analog for Output DAC B
(II) RADEONHD(0): Output TV_7PIN_DIN using monitor section Configured Monitor
(II) RADEONHD(0): Output VGA_1 has no monitor section
(II) RADEONHD(0): Output DVI-I_1/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_1/analog has no monitor section
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): Output TV_7PIN_DIN disconnected
(II) RADEONHD(0): Output VGA_1 disconnected
(II) RADEONHD(0): Output DVI-I_1/digital disconnected
(II) RADEONHD(0): Output DVI-I_1/analog connected
(II) RADEONHD(0): Output DVI-I_1/analog using initial mode 1280x768
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 1280x1280 Framebuffer with 1280 pitch
(==) RADEONHD(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) RADEONHD(0): Using ShadowFB
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdffe0000 - 0xdffeffff (0x10000) MS[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[7] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[8] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[9] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[10] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[11] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[12] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] 0	0	0x0000e000 - 0x0000e0ff (0x100) IS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[18] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[19] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[29] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[30] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[31] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) RADEONHD(0): Mapped IO at 0xb7add000 (size 0x00010000)
(==) RADEONHD(0): Write-combining range (0xe0000000,0x10000000)
(==) RADEONHD(0): Backing store disabled
(==) RADEONHD(0): Silken mouse enabled
(II) RADEONHD(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEONHD(0): RandR: While switching off TV_7PIN_DIN: output DAC B is also used by DVI-I_1/analog - ignoring
(WW) RADEONHD(0): RandR: While switching off TV_7PIN_DIN: output DAC B is also used by DVI-I_1/analog - ignoring
(II) RADEONHD(0): Using HW cursor
(II) RADEONHD(0): DPMS enabled
(--) RandR disabled
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
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) RADEONHD(0): Setting screen physical size to 338 x 203
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(WW) RADEONHD(0): RandR: While switching off TV_7PIN_DIN: output DAC B is also used by DVI-I_1/analog - ignoring
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): DAC B: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
```

theres alot of it, means nothing to me but, hope you guys can help with this!

---

### Post by Yellow Pasque on 2008-05-17
> (II) RADEONHD(0): Setting screen physical size to 338 x 203
Your monitor seems to be reporting random numbers when asked for the resolution :?

```
Section "Extensions"
	Option "Composite" "Off"
EndSection

Section "ServerFlags"
	Option "AIGLX" "Off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"radeonhd"
	BusID		"PCI:4:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1680x1050" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

You can add other modes in the Display subsection if your monitor is capable. You can also put mode lines in the Monitor Section generated by cvt. For example:
```
dan@harvest:/etc/X11$ cvt -v 1680 1050 60.0Hz
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
[B]Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
[/B]
```
Take the bolded line, change the '_' to a '@' and paste into your monitor section.

---

### Post by FoX_HunteR on 2008-05-18
ok, well i tried the xorg file you suplied, but it has no effect, even in the resolution options i cant change any of the info higher than what i had...

also, i dont quite undersdand where to put the bolded line for my monitor?
```
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

if anything i want the resolution at 1280x1024 72hz
the rest i dont really know much about,
also, the frame rate hasnt really improved all that much from what it was before in games and such...

---

### Post by FoX_HunteR on 2008-05-18
i noticed it had a bit of trouble switching between DVI and VGA, i was running a DVI>VGA adapter plug but now im just running it VGA,

but still no difference :(

---

### Post by FoX_HunteR on 2008-05-19
any help at all?

---

### Post by FoX_HunteR on 2008-05-20
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux da-beast-duo 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 20 20:02:08 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "AIGLX" "Off"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1043,817a rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1043,8290 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1043,8179 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1043,8179 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 1043,8179 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1043,8179 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1043,2601 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1043,8179 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:01:0: chip 168c,0013 card 168c,1051 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 1969,2048 card 1043,8233 rev a0 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,94c3 card 1043,01c2 rev 00 class 03,00,00 hdr 80
(II) PCI: 04:00:1: chip 1002,aa10 card 1043,aa10 rev 00 class 04,03,00 hdr 80
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
(II) Bus 4: bridge is at (0:1:0), (0,4,4), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xdff00000 - 0xdfffffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:0), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(4:0:0) ATI Technologies Inc unknown chipset (0x94c3) rev 0, Mem @ 0xe0000000/28, 0xdffe0000/16, I/O @ 0xe000/8, BIOS @ 0xdffc0000/17
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
	[0] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[1] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[2] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[3] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[4] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[5] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[6] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[9] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[10] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[11] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[12] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[20] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[21] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[22] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[1] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[2] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[3] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[4] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[5] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[6] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[9] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[10] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[11] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[12] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[13] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[20] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[21] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[22] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
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
	[4] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[5] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[6] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[7] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[8] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[9] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[10] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[26] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[27] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[28] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "radeonhd"
(II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.4.0.90, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
	RV505 : Radeon X1550, X1550 64bit.
	RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
	RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
	R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
	RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
	RV535 : Radeon X1300, X1650.
	RV550 : Radeon X2300 HD.
	RV560 : Radeon X1650.
	RV570 : Radeon X1950, X1950 GT; FireGL V7400.
	R580  : Radeon X1900, X1950; AMD Stream Processor.
	R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
	RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
	RV620 : Radeon HD 3450, HD 3470.
	RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
		FireGL V3600/V5600.
	RV635 : Radeon HD 3650, HD 3670.
	RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
	R680  : Radeon HD 3870 X2.
	M52   : Mobility Radeon X1300.
	M54   : Mobility Radeon X1400; M54-GL.
	M56   : Mobility Radeon X1600; Mobility FireGL V5200.
	M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
	M62   : Mobility Radeon X1350.
	M64   : Mobility Radeon X1450, X2300.
	M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
	M68   : Mobility Radeon X1900.
	M71   : Mobility Radeon HD 2300.
	M72   : Mobility Radeon HD 2400; Radeon E2400.
	M74   : Mobility Radeon HD 2400 XT.
	M76   : Mobility Radeon HD 2600;
		(Gemini ATI) Mobility Radeon HD 2600 XT.
	M82   : Mobility Radeon HD 3400.
	RS600 : Radeon Xpress 1200, Xpress 1250.
	RS690 : Radeon X1200, X1250, X1270.

(II) RADEONHD: version 1.2.1, built from git branch master, commit 867c8efa

(II) Primary Device is: PCI 04:00:0
(--) Chipset RV610 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[5] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[6] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[7] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[8] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[9] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[10] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[26] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[27] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[28] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[5] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[6] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[7] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[8] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[9] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[10] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[15] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[16] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[26] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[27] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[28] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[29] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(**) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Selected ShadowFB.
(II) RADEONHD(0): Unknown card detected: 0x94C3:0x1043:0x01C2.
	If - and only if - your card does not work or does not work optimally
	please contact radeonhd@opensuse.org to help rectify this.
	Use the subject: 0x94C3:0x1043:0x01C2: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an RV610 on an unidentified card
(II) RADEONHD(0): Mapped IO at 0xb7ab5000 (size 0x00010000)
(II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
(II) RADEONHD(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1043 SubsystemID: 0x01c2
	IOBaseAddress: 0xe000
	Filename: SV25680.BIN 
	BIOS Bootup Message: 

94C3.10.56.00.05.AS03                                                       


(II) RADEONHD(0): Analog TV Default Mode: 1
(II) RADEONHD(0): Found default TV Mode NTSC
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 16
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0xfffc000
(II) RADEONHD(0): AtomBIOS requests 16kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0xfffc000
(II) RADEONHD(0): Default Engine Clock: 525000
(II) RADEONHD(0): Default Memory Clock: 400000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.
(II) RADEONHD(0): PCI FB Address (BAR) is at 0x00000000 while card Internal Address is 0xE0000000
(II) RADEONHD(0): Mapped FB at (nil) (size 0x00000000)
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_TV, "7PIN_DIN TV1 CV", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACB, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_VGA, "VGA CRT1", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[2] {RHD_CONNECTOR_DVI, "DUAL_LINK_DVI_I DFP1 CRT2", RHD_DDC_1, RHD_HPD_0, { RHD_OUTPUT_LVTMA, RHD_OUTPUT_DACB } }
(--) RADEONHD(0): Attaching Output DAC B to Connector TV 7PIN_DIN
(--) RADEONHD(0): Attaching Output DAC A to Connector VGA 1
(--) RADEONHD(0): Attaching Output TMDS B to Connector DVI-I 1
(--) RADEONHD(0): Attaching Output DAC B to Connector DVI-I 1
(II) RADEONHD(0): RandR: Adding RRoutput TV_7PIN_DIN for Output DAC B
(II) RADEONHD(0): RandR: Adding RRoutput VGA_1 for Output DAC A
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/digital for Output TMDS B
(II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/analog for Output DAC B
(II) RADEONHD(0): Output TV_7PIN_DIN using monitor section Generic Monitor
(II) RADEONHD(0): Output VGA_1 has no monitor section
(II) RADEONHD(0): Output DVI-I_1/digital has no monitor section
(II) RADEONHD(0): Output DVI-I_1/analog has no monitor section
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): Output TV_7PIN_DIN disconnected
(II) RADEONHD(0): Output VGA_1 connected
(II) RADEONHD(0): Output DVI-I_1/digital connected
(II) RADEONHD(0): Output DVI-I_1/analog disconnected
(II) RADEONHD(0): Output VGA_1 using initial mode 1280x768
(II) RADEONHD(0): Output DVI-I_1/digital using initial mode 1280x768
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 1280x1280 Framebuffer with 1280 pitch
(==) RADEONHD(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) RADEONHD(0): Using ShadowFB
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdffe0000 - 0xdffeffff (0x10000) MS[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfffc000 - 0xdfffffff (0x4000) MX[B]
	[7] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B]
	[8] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[9] -1	0	0xdfcffc00 - 0xdfcfffff (0x400) MX[B]
	[10] -1	0	0xdfcf8000 - 0xdfcfbfff (0x4000) MX[B]
	[11] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B](B)
	[12] -1	0	0xdffe0000 - 0xdffeffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] 0	0	0x0000e000 - 0x0000e0ff (0x100) IS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[18] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[19] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[29] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[30] -1	0	0x00008400 - 0x0000841f (0x20) IX[B]
	[31] -1	0	0x00008000 - 0x0000801f (0x20) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B](B)
(II) RADEONHD(0): Mapped IO at 0xb7ab5000 (size 0x00010000)
(==) RADEONHD(0): Write-combining range (0xe0000000,0x10000000)
(==) RADEONHD(0): Backing store disabled
(==) RADEONHD(0): Silken mouse enabled
(II) RADEONHD(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) RADEONHD(0): Using HW cursor
(**) Option "dpms"
(**) RADEONHD(0): DPMS enabled
(--) RandR disabled
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
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) RADEONHD(0): Setting screen physical size to 338 x 203
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
(II) RADEONHD(0): DAC A: Sensed Output: VGA
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" removed.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" registered at address 0xA0.
(II) RADEONHD(0): I2C device "RHD I2C line 1:ddc2" removed.
```

i hope this helps can anyone help?
i really need it going

---

### Post by Yellow Pasque on 2008-05-21
> **FoX_HunteR said:**
>  i dont quite undersdand where to put the bolded line for my monitor?
Run this:
```
cvt -v 1280 1024 72.0Hz
```
Take the result and paste it into the Monitor Section of your /etc/X11/xorg.conf file. You can generate other mode lines in a similar fashion and paste them into Monitor Section as well.

---

### Post by FoX_HunteR on 2008-05-21
so, like this?

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Extensions"
	Option "Composite" "Off"
EndSection

Section "ServerFlags"
	Option "AIGLX" "Off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"radeonhd"
	BusID		"PCI:4:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline 	"1280x1024@72.00"  133.00  1280 1368 1504 1728  1024 1027 1034 1070 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection      "Display"
		Modes	"1680x1050" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

well im gunna try it, ill see how it goes...

---

### Post by FoX_HunteR on 2008-05-21
ok, it didnt do squat, its still exactly the same, im using the one in my previous post.

---

### Post by tormod on 2008-05-22
BTW, which version of -radeonhd are you using? You mention "rebuilding the xserver thingy", did you build it yourself from git? You can also find up to date drivers on [https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

---

### Post by FoX_HunteR on 2008-05-23
im very sure the drivers are the most up-to-date, and yes, i used git to rebuild the xserver, ill have a look for newer drivers but now that linux is on my pc i dont use it as much, so ill do it monday when the pc is used next. (its easier to use my motorola v6 on the net now)

---

### Post by FoX_HunteR on 2008-05-25
upgraded drivers to 1.2.1 today,
problem persists... any help?

---

### Post by tormod on 2008-05-25
> **FoX_HunteR said:**
> upgraded drivers to 1.2.1 today,
problem persists... any help?
You were already using 1.2.1 as seen from your logs, and if you were building from git, probably even a much newer version...

Try asking on #radeonhd or [email]radeonhd@opensuse.org[/email], they are usually very quick and helpful.

---

### Post by FoX_HunteR on 2008-05-27
well the new fglrx drivers have done the trick! so ill just use these for now, 3d works rather well but could be better...

---

