---
title: "Graphics card and LCD TV problems"
date: 2008-08-13
forum: Multimedia Software
---

### Post by jcr1 on 2008-08-13
Hi all.

I have a pc set up as a server with just Ubuntu 8.04 Desktop.

I have it plugged into my main LCD TV, just in case I need to see it (not via vnc etc).

I can VNC into no probs, and ssh. But the LCD TV won't pick it up or vice versa. The graphics card seems dodgey, not even sure what it is, but its onboard so nothing great, but I would expect it to be able to put something out my LCD TV would recognise. Its as if ubuntu hasn't detected the TV properly.

Not sure where to start really. I have had it working before, on a high res too, but can't get it going now.

I do know that glxinfo indicates NO direct rendering...

At the mo, when plugged into the TV it just flashes nothingness on screen... I expect its a out-of-range type signal.

---

### Post by jcr1 on 2008-08-18
Looking at my xorg log there are quite a lot of things (i dont understand) that look wrong to me.

There is a big section saying about all the standard resolutions not being able to work...so why are none of the standard resolution capable of displaying on my LCD TV... it should work with anything. My laptop displays no problem on the TV... but this PC doesn't.

Probably a crappy onboard graphics card to blame I am sure, but I would expect some normal resolutions to work. At the mo, none work!

Hope someone can help.

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux jcrserver 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 18 06:27:21 2008
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
(II) PCI: 00:00:0: chip 1039,0760 card 1043,8159 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0965 card 0000,0000 rev 47 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 1043,8139 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1043,810d rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1043,8139 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1043,8139 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 1043,8139 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1043,8139 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0190 card 1043,8139 rev 00 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0182 card 1043,8139 rev 01 class 01,04,85 hdr 00
(II) PCI: 00:06:0: chip 1039,000a card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1039,000a card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1039,6330 card 1043,8159 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe7f00000 - 0xf7efffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:6:0), (0,2,2), BCTRL: 0x0007 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:7:0), (0,3,3), BCTRL: 0x0007 (VGA_EN is cleared)
(--) PCI:*(1:0:0) Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter rev 0, Mem @ 0xe8000000/27, 0xfeae0000/17, I/O @ 0xbc00/7
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebf3c00 - 0xfebf3c7f (0x80) MX[B]
	[1] -1	0	0xfebf7000 - 0xfebf7fff (0x1000) MX[B]
	[2] -1	0	0xfebf6000 - 0xfebf6fff (0x1000) MX[B]
	[3] -1	0	0xfebf5000 - 0xfebf5fff (0x1000) MX[B]
	[4] -1	0	0xfebf4000 - 0xfebf4fff (0x1000) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[9] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebf3c00 - 0xfebf3c7f (0x80) MX[B]
	[1] -1	0	0xfebf7000 - 0xfebf7fff (0x1000) MX[B]
	[2] -1	0	0xfebf6000 - 0xfebf6fff (0x1000) MX[B]
	[3] -1	0	0xfebf5000 - 0xfebf5fff (0x1000) MX[B]
	[4] -1	0	0xfebf4000 - 0xfebf4fff (0x1000) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[9] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[10] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[12] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[13] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[14] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
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
	[4] -1	0	0xfebf3c00 - 0xfebf3c7f (0x80) MX[B]
	[5] -1	0	0xfebf7000 - 0xfebf7fff (0x1000) MX[B]
	[6] -1	0	0xfebf6000 - 0xfebf6fff (0x1000) MX[B]
	[7] -1	0	0xfebf5000 - 0xfebf5fff (0x1000) MX[B]
	[8] -1	0	0xfebf4000 - 0xfebf4fff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
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
(==) AIGLX enabled
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
(II) Matched sis from file name sis.ids in autoconfig
(==) Matched sis for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.9.3
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
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebf3c00 - 0xfebf3c7f (0x80) MX[B]
	[5] -1	0	0xfebf7000 - 0xfebf7fff (0x1000) MX[B]
	[6] -1	0	0xfebf6000 - 0xfebf6fff (0x1000) MX[B]
	[7] -1	0	0xfebf5000 - 0xfebf5fff (0x1000) MX[B]
	[8] -1	0	0xfebf4000 - 0xfebf4fff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[19] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[20] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebf3c00 - 0xfebf3c7f (0x80) MX[B]
	[5] -1	0	0xfebf7000 - 0xfebf7fff (0x1000) MX[B]
	[6] -1	0	0xfebf6000 - 0xfebf6fff (0x1000) MX[B]
	[7] -1	0	0xfebf5000 - 0xfebf5fff (0x1000) MX[B]
	[8] -1	0	0xfebf4000 - 0xfebf4fff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[21] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.4.0.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See http://www.winischhofer.at/linuxsisvga.shtml
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xBC00
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) SIS(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) SIS(0): Depth 24, (==) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(--) SIS(0): Video BIOS version "2.18.00" found (new SiS data layout)
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is enabled
(II) SIS(0): Using VRAM command queue, size 512k
(==) SIS(0): Hotkey display switching is enabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
		http://www.winischhofer.at/linuxsispart1.shtml#sisctrl
(==) SIS(0): DRI disabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(0): 32768K shared video RAM (UMA)
(--) SIS(0): DRAM type: DDR SDRAM
(--) SIS(0): Memory clock: 133.634 MHz
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xE8000000
(--) SIS(0): MMIO registers at 0xFEAE0000 (size 64K)
(--) SIS(0): VideoRAM: 32768 KB
(II) SIS(0): Using 32192K of framebuffer memory at offset 0K
(--) SIS(0): Hardware supports two video overlays
(II) SIS(0): 
	Dear SiS76x user, your machine is using a shared memory framebuffer.
	Due to hardware limitations of the SiS chip in combination with the
	AMD CPU, video overlay support is very limited on this machine. If you
	experience flashing lines in the video and/or the graphics display
	during video playback, reduce the color depth and/or the resolution
	and/or the refresh rate. Alternatively, use the video blitter.
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): Gamma correction is enabled
(II) SIS(0): Separate Xv gamma correction is disabled
(--) SIS(0): Memory bandwidth at 32 bpp is 267.268 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(--) SIS(0): CRT1 DDC probing failed
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 6330
(II) SIS(0): VESA VBE OEM Product Rev: 2.18.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) SIS(0): VESA VBE DDC supported
(II) SIS(0): VESA VBE DDC Level none
(II) SIS(0): VESA VBE DDC transfer in appr. 0 sec.
(II) SIS(0): VESA VBE DDC read failed
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 195 MHz
(II) SIS(0): Replaced entire mode list with built-in modes
(II) SIS(0): Using real widescreen modes for CRT1 VGA devices
(II) SIS(0): 	Use option "ForceCRT1VGAAspect" to overrule
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) SIS(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) SIS(0): Unable to estimate virtual size
(II) SIS(0): Clock range:  10.00 to 195.31 MHz
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x400" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "320x200" (vrefresh out of range)
(II) SIS(0): Not using default mode "512x384" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "800x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1024x576" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1400x1050" (hsync out of range)
(II) SIS(0): Not using default mode "1400x1050" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "848x480" (hsync out of range)
(II) SIS(0): Not using default mode "856x480" (hsync out of range)
(II) SIS(0): Not using default mode "1360x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1680x1050" (hsync out of range)
(II) SIS(0): Not using default mode "1280x854" (hsync out of range)
(II) SIS(0): Not using default mode "1280x854" (hsync out of range)
(II) SIS(0): Not using default mode "1280x854" (hsync out of range)
(--) SIS(0): Virtual size is 960x600 (pitch 960)
(**) SIS(0): *Default mode "960x600": 41.5 MHz, 37.1 kHz, 60.0 Hz
(II) SIS(0): Modeline "960x600"x60.0   41.50  960 1008 1088 1120  600 603 609 618 +hsync +vsync (37.1 kHz)
(**) SIS(0): *Default mode "960x540": 37.3 MHz, 33.8 kHz, 60.0 Hz
(II) SIS(0): Modeline "960x540"x60.0   37.29  960 976 1008 1104  540 543 549 563 +hsync +vsync (33.8 kHz)
(**) SIS(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(0): Modeline "800x600"x60.3   39.97  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "800x600": 36.1 MHz, 35.2 kHz, 56.3 Hz
(II) SIS(0): Modeline "800x600"x56.3   36.06  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SIS(0): *Default mode "768x576": 35.0 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "768x576"x60.1   35.00  768 792 872 976  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "720x576"x60.1   32.73  720 744 816 912  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(0): *Default mode "856x480": 33.9 MHz, 31.7 kHz, 59.8 Hz
(II) SIS(0): Modeline "856x480"x59.8   33.94  856 872 1000 1072  480 492 495 529 -hsync -vsync (31.7 kHz)
(**) SIS(0): *Default mode "800x480": 39.8 MHz, 37.7 kHz, 60.0 Hz
(II) SIS(0): Modeline "800x480"x60.0   39.77  800 840 968 1056  480 552 556 628 +hsync +vsync (37.7 kHz)
(**) SIS(0): *Default mode "720x480": 28.3 MHz, 31.6 kHz, 61.0 Hz
(II) SIS(0): Modeline "720x480"x61.0   28.28  720 728 840 896  480 490 492 517 -hsync -vsync (31.6 kHz)
(**) SIS(0): *Default mode "640x480": 25.1 MHz, 31.3 kHz, 59.7 Hz
(II) SIS(0): Modeline "640x480"x59.7   25.06  640 656 752 800  480 490 492 525 -hsync -vsync (31.3 kHz)
(**) SIS(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SIS(0): Modeline "400x300"x60.3   19.98  400 416 480 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SIS(0): *Default mode "320x240": 12.5 MHz, 31.3 kHz, 60.7 Hz (D)
(II) SIS(0): Modeline "320x240"x60.7   12.53  320 328 376 400  240 245 246 258 doublescan -hsync -vsync (31.3 kHz)
(==) SIS(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) SIS(0): 2D acceleration enabled
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B]
	[1] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfebf3c00 - 0xfebf3c7f (0x80) MX[B]
	[7] -1	0	0xfebf7000 - 0xfebf7fff (0x1000) MX[B]
	[8] -1	0	0xfebf6000 - 0xfebf6fff (0x1000) MX[B]
	[9] -1	0	0xfebf5000 - 0xfebf5fff (0x1000) MX[B]
	[10] -1	0	0xfebf4000 - 0xfebf4fff (0x1000) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[27] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 16384 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 6330
(II) SIS(0): VESA VBE OEM Product Rev: 2.18.00
(==) SIS(0): Write-combining range (0xe8000000,0x2000000)
(II) SIS(0): Setting standard mode 0x22
(II) SIS(0): SiS76x/UMA: one video overlay(s) available in current mode
(II) SIS(0): RENDER acceleration enabled
(II) SIS(0): Framebuffer from (0,0) to (959,8582)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		15 512x512 slots
		32 8x8 color pattern slots
(--) SIS(0): CPU frequency 1000.00Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0): 	Checked libc memcpy()... 	541.7 MiB/s
(--) SIS(0): 	Checked built-in-1 memcpy()... 	542.0 MiB/s
(--) SIS(0): 	Checked built-in-2 memcpy()... 	68.0 MiB/s
(--) SIS(0): 	Checked MMX memcpy()... 	534.5 MiB/s
(--) SIS(0): 	Checked 3DNow! memcpy()... 	538.8 MiB/s
(--) SIS(0): 	Checked MMX2 memcpy()... 	554.9 MiB/s
(--) SIS(0): Using MMX2 method for aligned data transfers to video RAM
(--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(II) SIS(0): DPMS enabled
(II) SIS(0): Using SiS300/315/330/340 series HW Xv
(II) SIS(0): Default Xv adaptor is Video Overlay
(WW) SIS(0): Option "UseFBDev" is not used
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
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
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

