---
title: "Resolution issue after switching Monitor videocard"
date: 2008-08-17
forum: Multimedia Software
---

### Post by Efaustus9 on 2008-08-17
I recently installed ubuntu 8.04 on an external hardrive from which I boot from at bios instead of making a partition on my internal harddisk. It detected the intel video card and CRT monitor of my home desktop just fine. I brought the external drive to a friends house and booted it up using his Nvidia video card and LCD monitor where it was also working well. However when I brought the drive back home and attempted to boot up ubuntu it no longer correctly identifies my home monitor resolution restricting me to either 640x480 or 800x600. I tried editing and restoring an old xorg.conf using sudo gedit xorg.conf but that doesnt work either. So any ideas anyone?

---

### Post by Efaustus9 on 2008-08-18
UPDATE: 

I looked at the output of my Xorg.0.log and its still trying to use the nvidia driver from my when I had the drive pluged into my friends computer. 

Xorg.0.log output:

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux evan 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 18 22:29:56 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) PCI: 00:00:0: chip 8086,2580 card 1028,0179 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2581 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2582 card 1028,0179 rev 04 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2782 card 1028,0179 rev 04 class 03,80,00 hdr 80
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1028,0179 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1028,0179 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1028,0179 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1028,0179 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1028,0179 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 1028,0179 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2640 card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1028,0179 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 1028,0179 rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 1028,0179 rev 03 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,1677 card 1028,0179 rev 01 class 02,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfdfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdfb00000 - 0xdfbfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0xdff00000/19, 0xc0000000/28, 0xdfec0000/18, I/O @ 0xe898/3
(--) PCI: (0:2:1) Intel Corporation 82915G Integrated Graphics Controller rev 4, Mem @ 0xdff80000/19
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
	[0] -1	0	0xdfcf0000 - 0xdfcfffff (0x10000) MX[B]
	[1] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[2] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[5] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[23] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[24] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[25] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfcf0000 - 0xdfcfffff (0x10000) MX[B]
	[1] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[2] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[3] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[4] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[5] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[6] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[8] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[9] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[10] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[11] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[12] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[13] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[23] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[24] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[25] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
	[4] -1	0	0xdfcf0000 - 0xdfcfffff (0x10000) MX[B]
	[5] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[6] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[9] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[15] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[16] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[17] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[18] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[19] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
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
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.05  Tue Jan 22 20:11:30 PST 2008
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
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 915G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcf0000 - 0xdfcfffff (0x10000) MX[B]
	[5] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[6] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[9] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[15] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[16] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[17] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[18] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[19] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[22] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[23] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[29] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[30] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[31] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcf0000 - 0xdfcfffff (0x10000) MX[B]
	[5] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[6] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[9] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[18] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[25] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[26] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[32] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[33] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[34] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 915G
(--) intel(0): Chipset: "915G"
(--) intel(0): Linear framebuffer at 0xC0000000
(--) intel(0): IO registers at addr 0xDFF00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (320, 240) mm
(**) intel(0): DPI set to (101, 135)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfec0000 - 0xdfefffff (0x40000) MS[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[2] 0	0	0xdff00000 - 0xdff7ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfcf0000 - 0xdfcfffff (0x10000) MX[B]
	[8] -1	0	0xdfebfd00 - 0xdfebfdff (0x100) MX[B]
	[9] -1	0	0xdfebfe00 - 0xdfebffff (0x200) MX[B]
	[10] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[11] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[12] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] 0	0	0x0000e898 - 0x0000e89f (0x8) IS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e8a0 - 0x0000e8bf (0x20) IX[B]
	[22] -1	0	0x0000fea0 - 0x0000feaf (0x10) IX[B]
	[23] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[24] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[25] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[26] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[29] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[30] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000e8c0 - 0x0000e8ff (0x40) IX[B]
	[33] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
	[34] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[35] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[36] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[37] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[38] -1	0	0x0000e898 - 0x0000e89f (0x8) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 301056 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1204220 kB available
(EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x000000004f820000 physical
)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x000000004f832000 physical
)
(II) intel(0): 0x00040000-0x0067ffff: front buffer (6400 kB)
(II) intel(0): 0x00680000-0x0193ffff: exa offscreen (19200 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Disabled
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
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) intel(0): Setting screen physical size to 320 x 240
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  107.01  1280 1320 1424 1664  1024 1037 1040 1072 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "640x400"x0.0   25.26  640 657 753 800  400 412 413 450 -hsync +vsync (31.6 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "TRL", prod id 1296
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9

from this line here:

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"

it seems I am still using the Nvidia driver so how do I revert it back to the integrated lintel one.

---

### Post by chemist109 on 2008-08-19
This should get rid of nvidia's GLX:

```
sudo apt-get remove --purge nvidia-glx*
```

I'm not sure that it's your only problem, though.

---

### Post by Zimmer on 2008-08-20
Similar resolution issue (still searching for answers) just installed Hardy fresh (former Dapper user) and considering going back due to Xorg changes.
Check your log in case for monitor issues (your log full of duplicated modelines looks similar to this ):

Had monitor on a VGA extension cable and initial res on login was abve the usual native res of monitor 1024x768 and showed a black space on right... once logged in it played nice in 1024x768.

Plugged the monitor direct into the video card and a tale of woe ensues.
640x350 and at that res I cannot access the gui to change the res !!! 
The xorg log indicates that on the extension lead it cannot detect the EDID settings for the monitor so uses a generic setup...

Plugged in properly the monitor is detected and the log shows the EDID but about 3 times over as though it is in a loop. I think it must then failsafe... cannot quite tell from the log .  

Tried putting the monitor settings in the xorg.conf  no difference. The latest xorg 1.4 works differently by detecting hardware using HAL, I think and is trying to do away with the xorg.conf file....

Away to search more threads..
and found this:
sudo xrandr -s 1024x768
puts the screen in the right res. And a quick visit to Preferences>Screen res  and I can pop it into 60hz to fill the screen as usual.
This sticks to the next reboot. But the login screen is still at an illegible 640x350 . Not happy yet.

See this,too.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760)

---

