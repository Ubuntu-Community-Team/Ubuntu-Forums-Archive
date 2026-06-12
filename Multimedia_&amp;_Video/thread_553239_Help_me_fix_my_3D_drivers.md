---
title: "Help me fix my 3D drivers"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by Deived on 2007-09-17
Help!

I tried installing the latest ATI drivers that I got from the ati.amd site.  My mistake, I didn't run the installation the way the instructions said.  It says to download the .run file and convert it to a debian package and install.  I just ran the .run file and it installed, but I have no idea what it put where.  It fails to start X when I reboot.  It gives some kind of kernel error or something about not being able to use it with that kernel (I'm in Feisty).  Anyway, I can get back into X by changing the driver in xorg.conf from fglrx to ati, but I can't use any 3d anymore.  I tried taking away all the packages and reinstalling the driver the right way, but I get the same thing.  I was able to use the restricted driver manager before to enable the 3d, but not since I tried to update it.

My question is, I'm not sure what the .run file did, so is there any way I can remove everything and put back the Ubuntu supported stuff?  Sorry I cant give much more detail, but I'm at work and my computer is at home.  Also, are there any error logs that I could post that might help?  (I still haven't quite figured out where all the error logs are.  Everything seems to put them in different places).

I hope im making sense... I'm trying to write this quickly.

---

### Post by kellemes on 2007-09-17
Logs are in /var/log
watch Xorg.0.log closely..

---

### Post by Deived on 2007-09-19
I took a look, but I can't quite figure it out.  I removed restricted-drivers and everything fglrx, did and apt-get clean autoclean and autoremove to make sure Im not installing already downloaded packages.  
I installed restricted-drivers back and enable the ati restricted driver.  When I reboot, I get into X now, and it looks like I'm using the right driver (fonts are a tad smaller) but I get no 3D acceleration.  Can anyone help?  I really don't know what to try next.
Here's my Xorg.0.log

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux david-laptop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 18 20:52:55 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies Inc M22 [Radeon Mobility M300]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 8086,2590 card 1028,0188 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2591 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,2658 card 1028,0188 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1028,0188 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1028,0188 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1028,0188 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1028,0188 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d3 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 1028,0188 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1e:3: chip 8086,266d card 14f1,5423 rev 03 class 07,03,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2641 card 1028,0188 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2653 card 1028,0188 rev 03 class 01,01,80 hdr 00
(II) PCI: 01:00:0: chip 1002,5460 card 1028,2003 rev 00 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,170c card 1028,0188 rev 02 class 02,00,00 hdr 00
(II) PCI: 03:01:0: chip 1180,0476 card 2000,0000 rev b3 class 06,07,00 hdr 82
(II) PCI: 03:01:1: chip 1180,0552 card 1028,0188 rev 08 class 0c,00,10 hdr 80
(II) PCI: 03:01:2: chip 1180,0822 card 1028,0188 rev 17 class 08,05,01 hdr 80
(II) PCI: 03:03:0: chip 8086,4223 card 8086,1020 rev 05 class 02,80,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,7), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfcfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x60000000 - 0x63ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:1:0), (3,4,7), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x60000000 - 0x63ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc M22 [Radeon Mobility M300] rev 0, Mem @ 0xd0000000/27, 0xdfdf0000/16, I/O @ 0xde00/8
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
	[0] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[1] -1	0	0xdfcfc700 - 0xdfcfc7ff (0x100) MX[B]
	[2] -1	0	0xdfcfc800 - 0xdfcfcfff (0x800) MX[B]
	[3] -1	0	0xdfcfe000 - 0xdfcfffff (0x2000) MX[B]
	[4] -1	0	0xdffffd00 - 0xdffffdff (0x100) MX[B]
	[5] -1	0	0xdffffe00 - 0xdfffffff (0x200) MX[B]
	[6] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[7] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[10] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[11] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[12] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[15] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[16] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[17] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[1] -1	0	0xdfcfc700 - 0xdfcfc7ff (0x100) MX[B]
	[2] -1	0	0xdfcfc800 - 0xdfcfcfff (0x800) MX[B]
	[3] -1	0	0xdfcfe000 - 0xdfcfffff (0x2000) MX[B]
	[4] -1	0	0xdffffd00 - 0xdffffdff (0x100) MX[B]
	[5] -1	0	0xdffffe00 - 0xdfffffff (0x200) MX[B]
	[6] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[7] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[10] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[11] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[12] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[14] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[15] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[16] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[17] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
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
	[4] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[5] -1	0	0xdfcfc700 - 0xdfcfc7ff (0x100) MX[B]
	[6] -1	0	0xdfcfc800 - 0xdfcfcfff (0x800) MX[B]
	[7] -1	0	0xdfcfe000 - 0xdfcfffff (0x2000) MX[B]
	[8] -1	0	0xdffffd00 - 0xdffffdff (0x100) MX[B]
	[9] -1	0	0xdffffe00 - 0xdfffffff (0x200) MX[B]
	[10] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[11] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[16] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[17] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[18] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[21] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[22] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[23] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.34.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.34g1                           
(II) ATI Proprietary Linux Driver Build Date: Feb 20 2007 11:49:19
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.34.1.1.2.3-driver-lnx-x86-x86_64-327152
(--) Chipset Supported AMD Graphics Processor (0x5460) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[5] -1	0	0xdfcfc700 - 0xdfcfc7ff (0x100) MX[B]
	[6] -1	0	0xdfcfc800 - 0xdfcfcfff (0x800) MX[B]
	[7] -1	0	0xdfcfe000 - 0xdfcfffff (0x2000) MX[B]
	[8] -1	0	0xdffffd00 - 0xdffffdff (0x100) MX[B]
	[9] -1	0	0xdffffe00 - 0xdfffffff (0x200) MX[B]
	[10] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[11] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[16] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[17] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[18] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[21] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[22] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[23] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e6860
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[5] -1	0	0xdfcfc700 - 0xdfcfc7ff (0x100) MX[B]
	[6] -1	0	0xdfcfc800 - 0xdfcfcfff (0x800) MX[B]
	[7] -1	0	0xdfcfe000 - 0xdfcfffff (0x2000) MX[B]
	[8] -1	0	0xdffffd00 - 0xdffffdff (0x100) MX[B]
	[9] -1	0	0xdffffe00 - 0xdfffffff (0x200) MX[B]
	[10] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[11] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[19] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[20] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[21] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[24] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[25] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[26] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[27] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[28] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[29] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[30] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[31] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "ATI MOBILITY RADEON X300" (Chipset = 0x5460)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x2003)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xdfdf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 65536 kB
(II) fglrx(0): VESA VBE OEM: ATI MOBILITY RADEON (M24)  
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: P22 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.34.8
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
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
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 71.1 MHz   Image Size:  0 x 0 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00367f000000000000
(II) fglrx(0): 	0000010380281e00f200000000000000
(II) fglrx(0): 	00000021080031404540614000000000
(II) fglrx(0): 	000000000000c71b00a0502017303020
(II) fglrx(0): 	26000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000000
(II) fglrx(0): 	00000000000000000000000000000026
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 297/216MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 100/122MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 105/182MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0):   4. 209/182MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   5. 209/182MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 14 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1328 1360 1440  800 802 808 823
(**) fglrx(0):  Default mode "1280x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   71.11  1280 1328 1360 1440  768 786 792 823
(**) fglrx(0):  Default mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1200 1232 1440  768 786 792 823
(**) fglrx(0):  Default mode "848x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.11  848 1112 1144 1440  480 642 648 823
(**) fglrx(0):  Default mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1088 1120 1440  600 702 708 823
(**) fglrx(0):  Default mode "720x576": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   71.11  720 1048 1080 1440  576 690 696 823
(**) fglrx(0):  Default mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1048 1080 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 1008 1040 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 1008 1040 1440  400 602 608 823
(**) fglrx(0):  Default mode "640x350": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.11  640 1008 1040 1440  350 577 583 823
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 944 976 1440  384 594 600 823
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.11  400 888 920 1440  300 702 708 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.11  320 848 880 1440  240 642 648 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.11  320 848 880 1440  200 602 608 823 doublescan
(--) fglrx(0): Display dimensions: (400, 300) mm
(--) fglrx(0): DPI set to (81, 67)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   71.11  1280 1328 1360 1440  800 802 808 823
(**) fglrx(0):  Default mode "1280x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   71.11  1280 1328 1360 1440  768 786 792 823
(**) fglrx(0):  Default mode "1024x768": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   71.11  1024 1200 1232 1440  768 786 792 823
(**) fglrx(0):  Default mode "848x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "848x480"   71.11  848 1112 1144 1440  480 642 648 823
(**) fglrx(0):  Default mode "800x600": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   71.11  800 1088 1120 1440  600 702 708 823
(**) fglrx(0):  Default mode "720x576": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x576"   71.11  720 1048 1080 1440  576 690 696 823
(**) fglrx(0):  Default mode "720x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   71.11  720 1048 1080 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x480": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   71.11  640 1008 1040 1440  480 642 648 823
(**) fglrx(0):  Default mode "640x400": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   71.11  640 1008 1040 1440  400 602 608 823
(**) fglrx(0):  Default mode "640x350": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x350"   71.11  640 1008 1040 1440  350 577 583 823
(**) fglrx(0):  Default mode "512x384": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   71.11  512 944 976 1440  384 594 600 823
(**) fglrx(0):  Default mode "400x300": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   71.11  400 888 920 1440  300 702 708 823 doublescan
(**) fglrx(0):  Default mode "320x240": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   71.11  320 848 880 1440  240 642 648 823 doublescan
(**) fglrx(0):  Default mode "320x200": 71.1 MHz (scaled from 0.0 MHz), 49.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   71.11  320 848 880 1440  200 602 608 823 doublescan
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
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(II) fglrx(0): [pcie] 126976 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfcfd000 - 0xdfcfdfff (0x1000) MX[B]
	[7] -1	0	0xdfcfc700 - 0xdfcfc7ff (0x100) MX[B]
	[8] -1	0	0xdfcfc800 - 0xdfcfcfff (0x800) MX[B]
	[9] -1	0	0xdfcfe000 - 0xdfcfffff (0x2000) MX[B]
	[10] -1	0	0xdffffd00 - 0xdffffdff (0x100) MX[B]
	[11] -1	0	0xdffffe00 - 0xdfffffff (0x200) MX[B]
	[12] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[13] -1	0	0xdfdf0000 - 0xdfdfffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[18] 0	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000ec80 - 0x0000ecff (0x80) IX[B]
	[27] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[28] -1	0	0x0000ec40 - 0x0000ec7f (0x40) IX[B]
	[29] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[30] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[31] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[32] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[33] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[34] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7381000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.40.4
(II) fglrx(0):     Date: Jul 31 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7381000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x03fe0000
(II) fglrx(0): Splitting WC range: base: 0xd0000000, size: 0x3fe0000
(II) fglrx(0): Splitting WC range: base: 0xd2000000, size: 0x1fe0000
(II) fglrx(0): Splitting WC range: base: 0xd3000000, size: 0xfe0000
(II) fglrx(0): Splitting WC range: base: 0xd3800000, size: 0x7e0000
(II) fglrx(0): Splitting WC range: base: 0xd3c00000, size: 0x3e0000
(II) fglrx(0): Splitting WC range: base: 0xd3e00000, size: 0x1e0000
(II) fglrx(0): Splitting WC range: base: 0xd3f00000, size: 0xe0000
(II) fglrx(0): Splitting WC range: base: 0xd3f80000, size: 0x60000
(==) fglrx(0): Write-combining range (0xd3fc0000,0x20000)
(==) fglrx(0): Write-combining range (0xd3f80000,0x60000)
(==) fglrx(0): Write-combining range (0xd3f00000,0xe0000)
(==) fglrx(0): Write-combining range (0xd3e00000,0x1e0000)
(==) fglrx(0): Write-combining range (0xd3c00000,0x3e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd3800000,0x7e0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd3000000,0xfe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd2000000,0x1fe0000)
(WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x3fe0000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7391
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
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
(==) fglrx(0): Using hardware cursor
fbarea0->box.x1 0x00000000, fbarea0->box.y1 0x00000324
fbarea0->box.x2 0x00000500, fbarea0->box.y2 0x00000326
icon[0].start=0x3ed000
fbarea1->box.x1 0x00000000, fbarea1->box.y1 0x00000326
fbarea1->box.x2 0x00000500, fbarea1->box.y2 0x00000328
icon[1].start=0x3f0000
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
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
(**) Configured Mouse: Buttons: 9
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?
```

And my xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc M22 [Radeon Mobility M300]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M22 [Radeon Mobility M300]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

---

### Post by Deived on 2007-09-19
Hopefully I'm looking at it right.
The line that stands our for me...

```
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
```

---

