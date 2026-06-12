---
title: "Black Screen after Login"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by rustikus on 2007-04-26
Hi,

i have a weird problem with my new Ubuntu Installation. After i logged in from GDM for the first time the screen turns black and i neither can switch to a virtual terminal nor connect via ssh. The system seems to be completely "down". 

The strange thing is that the problem disappears when i press the reset button and reboot the system. Unfortunately i can not find any hint in the logfiles.

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux lv-426 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 26 21:41:00 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Monitor Screen" (0)
(**) |   |-->Monitor "Monitor"
(**) |   |-->Device "NVMonitor"
(**) |-->Screen "TV Screen" (1)
(**) |   |-->Monitor "TV"
(**) |   |-->Device "NVTV"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "MX1000"
(II) No default mouse found, adding one
(**) |-->Input Device "<default pointer>"
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
(**) Option "Xinerama" "off"
(**) Extension "Composite" is enabled
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
(II) PCI: 00:00:0: chip 10de,005e card 1043,815a rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1043,815a rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1043,815a rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1043,815a rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1043,815a rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0059 card 1043,812a rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,0053 card 1043,815a rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1043,815a rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1043,8141 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0291 card 1458,3424 rev a1 class 03,00,00 hdr 00
(II) PCI: 05:08:0: chip 109e,036e card 0070,13eb rev 11 class 04,00,00 hdr 80
(II) PCI: 05:08:1: chip 109e,0878 card 0070,13eb rev 11 class 04,80,00 hdr 80
(II) PCI: 05:0a:0: chip 1095,3114 card 1043,8167 rev 02 class 01,04,00 hdr 00
(II) PCI: 05:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:9:0), (0,5,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00008000 - 0x00009fff (0x2000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xc3000000 - 0xc4ffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xc5000000 - 0xc50fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:11:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:13:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:14:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xc2ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7900 GT rev 161, Mem @ 0xc0000000/24, 0xb0000000/28, 0xc1000000/24, I/O @ 0xa000/7, BIOS @ 0xc2000000/17
(--) PCI: (5:8:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xc5000000/12
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
	[0] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[1] -1	0	0xc4004000 - 0xc40047ff (0x800) MX[B]
	[2] -1	0	0xc4005000 - 0xc40053ff (0x400) MX[B]
	[3] -1	0	0xc5001000 - 0xc5001fff (0x1000) MX[B]
	[4] -1	0	0xc5100000 - 0xc5100fff (0x1000) MX[B]
	[5] -1	0	0xc5101000 - 0xc5101fff (0x1000) MX[B]
	[6] -1	0	0xc5102000 - 0xc5102fff (0x1000) MX[B]
	[7] -1	0	0xc5103000 - 0xc5103fff (0x1000) MX[B]
	[8] -1	0	0xc5105000 - 0xc51050ff (0x100) MX[B]
	[9] -1	0	0xc5104000 - 0xc5104fff (0x1000) MX[B]
	[10] -1	0	0xc5000000 - 0xc5000fff (0x1000) MX[B](B)
	[11] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)
	[12] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[16] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[17] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[18] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[19] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[34] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[35] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[1] -1	0	0xc4004000 - 0xc40047ff (0x800) MX[B]
	[2] -1	0	0xc4005000 - 0xc40053ff (0x400) MX[B]
	[3] -1	0	0xc5001000 - 0xc5001fff (0x1000) MX[B]
	[4] -1	0	0xc5100000 - 0xc5100fff (0x1000) MX[B]
	[5] -1	0	0xc5101000 - 0xc5101fff (0x1000) MX[B]
	[6] -1	0	0xc5102000 - 0xc5102fff (0x1000) MX[B]
	[7] -1	0	0xc5103000 - 0xc5103fff (0x1000) MX[B]
	[8] -1	0	0xc5105000 - 0xc51050ff (0x100) MX[B]
	[9] -1	0	0xc5104000 - 0xc5104fff (0x1000) MX[B]
	[10] -1	0	0xc5000000 - 0xc5000fff (0x1000) MX[B](B)
	[11] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)
	[12] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)
	[15] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[16] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[17] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[18] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[19] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[34] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[35] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
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
	[4] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[5] -1	0	0xc4004000 - 0xc40047ff (0x800) MX[B]
	[6] -1	0	0xc4005000 - 0xc40053ff (0x400) MX[B]
	[7] -1	0	0xc5001000 - 0xc5001fff (0x1000) MX[B]
	[8] -1	0	0xc5100000 - 0xc5100fff (0x1000) MX[B]
	[9] -1	0	0xc5101000 - 0xc5101fff (0x1000) MX[B]
	[10] -1	0	0xc5102000 - 0xc5102fff (0x1000) MX[B]
	[11] -1	0	0xc5103000 - 0xc5103fff (0x1000) MX[B]
	[12] -1	0	0xc5105000 - 0xc51050ff (0x100) MX[B]
	[13] -1	0	0xc5104000 - 0xc5104fff (0x1000) MX[B]
	[14] -1	0	0xc5000000 - 0xc5000fff (0x1000) MX[B](B)
	[15] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)
	[16] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[22] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[23] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[24] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[25] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[28] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[29] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[30] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[31] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[33] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[34] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[35] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[36] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[37] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[38] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[39] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[40] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[41] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[42] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[43] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
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
	[4] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[5] -1	0	0xc4004000 - 0xc40047ff (0x800) MX[B]
	[6] -1	0	0xc4005000 - 0xc40053ff (0x400) MX[B]
	[7] -1	0	0xc5001000 - 0xc5001fff (0x1000) MX[B]
	[8] -1	0	0xc5100000 - 0xc5100fff (0x1000) MX[B]
	[9] -1	0	0xc5101000 - 0xc5101fff (0x1000) MX[B]
	[10] -1	0	0xc5102000 - 0xc5102fff (0x1000) MX[B]
	[11] -1	0	0xc5103000 - 0xc5103fff (0x1000) MX[B]
	[12] -1	0	0xc5105000 - 0xc51050ff (0x100) MX[B]
	[13] -1	0	0xc5104000 - 0xc5104fff (0x1000) MX[B]
	[14] -1	0	0xc5000000 - 0xc5000fff (0x1000) MX[B](B)
	[15] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)
	[16] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[22] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[23] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[24] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[25] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[28] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[29] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[30] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[31] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[32] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[33] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[34] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[35] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[36] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[37] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[38] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[39] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[40] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[41] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[42] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[43] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[5] -1	0	0xc4004000 - 0xc40047ff (0x800) MX[B]
	[6] -1	0	0xc4005000 - 0xc40053ff (0x400) MX[B]
	[7] -1	0	0xc5001000 - 0xc5001fff (0x1000) MX[B]
	[8] -1	0	0xc5100000 - 0xc5100fff (0x1000) MX[B]
	[9] -1	0	0xc5101000 - 0xc5101fff (0x1000) MX[B]
	[10] -1	0	0xc5102000 - 0xc5102fff (0x1000) MX[B]
	[11] -1	0	0xc5103000 - 0xc5103fff (0x1000) MX[B]
	[12] -1	0	0xc5105000 - 0xc51050ff (0x100) MX[B]
	[13] -1	0	0xc5104000 - 0xc5104fff (0x1000) MX[B]
	[14] -1	0	0xc5000000 - 0xc5000fff (0x1000) MX[B](B)
	[15] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)
	[16] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[17] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[25] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[26] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[27] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[28] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[31] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[32] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[33] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[34] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[36] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[37] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[38] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[39] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[40] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[41] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[42] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[43] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[44] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[45] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[46] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[47] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[48] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo"
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GT/GTO at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.29.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GT/GTO at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-1)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "TV"
(**) NVIDIA(1): Option "TVStandard" "PAL-B"
(**) NVIDIA(1): Option "TVOutFormat" "S-VIDEO"
(**) NVIDIA(1): Option "TwinView" "1"
(**) NVIDIA(1): Option "TwinViewOrientation" "Clone"
(**) NVIDIA(1): Option "MetaModes" "640x480"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Unknown TVOutFormat value.  Known values are"AUTOSELECT",
(**) NVIDIA(1):     "COMPOSITE", "SVIDEO", "COMPONENT", "SCART"
(**) NVIDIA(1): TV Standard string: "PAL-B"
(**) NVIDIA(1): TwinView enabled
(II) NVIDIA(1): NVIDIA GPU GeForce 7900 GT/GTO at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.71.22.29.00
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 7900 GT/GTO at
(--) NVIDIA(1):     PCI:1:0:0:
(--) NVIDIA(1):     Samsung SyncMaster (CRT-1)
(--) NVIDIA(1):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(1): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): TV encoder: NVIDIA
(WW) NVIDIA(1): TwinView requested, but only 1 display devices found.
(II) NVIDIA(1): Assigned Display Device: TV-0
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "640x480"
(II) NVIDIA(1): Virtual screen size determined to be 640 x 480
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(WW) NVIDIA(1): Unable to load "xf86ExecX86int10".
(EE) NVIDIA(1): Unable to initialize the X Int10 module; the console may not
(EE) NVIDIA(1):     be restored correctly on your TV.
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B]
	[1] 0	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
	[2] 0	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xc4000000 - 0xc4003fff (0x4000) MX[B]
	[8] -1	0	0xc4004000 - 0xc40047ff (0x800) MX[B]
	[9] -1	0	0xc4005000 - 0xc40053ff (0x400) MX[B]
	[10] -1	0	0xc5001000 - 0xc5001fff (0x1000) MX[B]
	[11] -1	0	0xc5100000 - 0xc5100fff (0x1000) MX[B]
	[12] -1	0	0xc5101000 - 0xc5101fff (0x1000) MX[B]
	[13] -1	0	0xc5102000 - 0xc5102fff (0x1000) MX[B]
	[14] -1	0	0xc5103000 - 0xc5103fff (0x1000) MX[B]
	[15] -1	0	0xc5105000 - 0xc51050ff (0x100) MX[B]
	[16] -1	0	0xc5104000 - 0xc5104fff (0x1000) MX[B]
	[17] -1	0	0xc5000000 - 0xc5000fff (0x1000) MX[B](B)
	[18] -1	0	0xc2000000 - 0xc201ffff (0x20000) MX[B](B)
	[19] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[20] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xc0000000 - 0xc0ffffff (0x1000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] 0	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[29] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[30] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[31] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[32] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[35] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[36] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[37] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[38] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[39] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[40] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[41] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[42] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[43] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[44] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[45] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[46] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[47] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[48] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[49] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[50] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[51] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[52] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Built-in logo is bigger than the screen.
(II) NVIDIA(1): Setting mode "640x480"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbVariant" "nodeadkeys"
(**) Generic Keyboard: XkbVariant: "nodeadkeys"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) MX1000-usb-0000:00:02.0-2/input0: Core Pointer
(II) MX1000-usb-0000:00:02.0-2/input0: Found 3 relative axes.
(II) MX1000-usb-0000:00:02.0-2/input0: Configuring as pointer.
(**) MX1000-usb-0000:00:02.0-2/input0: WHEELRelativeAxisButtons: 4 5.
(II) MX1000-usb-0000:00:02.0-2/input0: Found 16 mouse buttons
(**) MX1000-usb-0000:00:02.0-2/input0: Configuring 3 relative axes.
(II) MX1000-usb-0000:00:02.0-2/input0: Configured 18 mouse buttons
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "MX1000-usb-0000:00:02.0-2/input0" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) MX1000-usb-0000:00:02.0-2/input0: 3 valuators.
(**) ../../src/evdev_btn.c (166): Registering 18 buttons.
(II) MX1000-usb-0000:00:02.0-2/input0: Init
(II) evdev brain: Rescanning devices (2).
(II) MX1000-usb-0000:00:02.0-2/input0: On
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?


```

Any hints?

Thanks,
rustikus

---

### Post by rustikus on 2007-04-27
I forget to attach the xorg.conf. 

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

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
#Section "ServerLayout"
#    Identifier     "Default Layout"
#    Screen         "Default Screen" 0 0
#    InputDevice    "Generic Keyboard"
#    InputDevice    "Configured Mouse"
#EndSection

Section "ServerLayout"

#     InputDevice    "Configured Mouse"
    Identifier     "Default Layout"
    Screen      0  "Monitor Screen" 0 0
    Screen      1  "TV Screen" LeftOf "Monitor Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "MX1000"
EndSection

Section "ServerLayout"

#     InputDevice 	"Configured Mouse"
    Identifier     "single"
    Screen         "Monitor Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "MX1000"
EndSection

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
# 	Load	"dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "ServerFlags"

##########	TwinView
#        Option    "RandR"       "true"
#        Option    "Xinerama"    "true"
    Option         "Clone" "on"
    Option         "Xinerama" "off"
##########
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
    Identifier     "MX1000"
    Driver         "evdev"
    Option         "CorePointer"
    Option         "Name" "Logitech USB Receiver"
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

Section "Monitor"

    # Optimal resolution for Samsung Syncmaster 171S TFT
    # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
    Identifier     "Monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    ModeLine       "1280x1024_60.00" 108.9 1280 1360 1496 1712 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1280x1024_76.00" 141.8 1280 1376 1512 1744 1024 1025 1028 1070 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "TV"
    HorizSync       30.0 - 40.0
    VertRefresh     50.0
EndSection

Section "Device"
    Identifier     "NVMonitor"
    Driver         "nvidia"
    BoardName      "nVidia Corporation G71 [GeForce 7900 GT/GTO]"
    Option 	   "AddARGBGLXVisuals" "True"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

##########	TwinView  
    Identifier     "NVTV"
    Driver         "nvidia"
    BoardName      "nVidia Corporation G71 [GeForce 7900 GT/GTO]"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Monitor Screen"
    Device         "NVMonitor"
    Monitor        "Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "NoLogo"
    Option         "NvAgp" "1"
    Option         "AllowGLXWithComposite" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "TV Screen"
    Device         "NVTV"
    Monitor        "TV"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewOrientation" "Clone"
    Option         "MetaModes" "640x480"
##########
    Option         "ConnectedMonitor" "TV"
    Option         "TVStandard" "PAL-B"
    Option         "TVOutFormat" "S-VIDEO"
    SubSection     "Display"
        Depth       24
        Modes      "800x600" "720x576"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by rustikus on 2007-04-28
I attached the /var/log/messages but i didn't find anything useful.

```

Apr 28 10:24:46 lv-426 kernel: [   74.524709] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (version 2.00.00)
Apr 28 10:24:46 lv-426 kernel: [   74.524756] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
Apr 28 10:24:46 lv-426 kernel: [   74.524759] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
Apr 28 10:24:46 lv-426 kernel: [   74.524761] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
Apr 28 10:24:46 lv-426 kernel: [   74.524763] powernow-k8: invalid freq entries 3900000 kHz vs. 65535000 kHz
Apr 28 10:24:46 lv-426 kernel: [   74.524766] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
Apr 28 10:24:46 lv-426 kernel: [   74.524768] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
Apr 28 10:24:46 lv-426 kernel: [   74.524770] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0xa
Apr 28 10:24:49 lv-426 dhcdbd: Started up.
Apr 28 10:24:49 lv-426 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr 28 10:24:49 lv-426 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr 28 10:24:49 lv-426 kernel: [   78.427361] ppdev: user-space parallel port driver
Apr 28 10:24:50 lv-426 hpiod: 1.7.3 accepting connections at 2208... 
Apr 28 10:24:51 lv-426 kernel: [   79.517412] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
Apr 28 10:24:51 lv-426 kernel: [   79.517858] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
Apr 28 10:24:51 lv-426 kernel: [   79.518153] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!
Apr 28 10:24:51 lv-426 kernel: [   80.456371] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Apr 28 10:24:51 lv-426 kernel: [   80.456375] apm: overridden by ACPI.
Apr 28 10:24:53 lv-426 kernel: [   81.600620] bridge-eth0: already up
Apr 28 10:24:53 lv-426 kernel: [   81.795436] Bluetooth: Core ver 2.11
Apr 28 10:24:53 lv-426 kernel: [   81.795495] NET: Registered protocol family 31
Apr 28 10:24:53 lv-426 kernel: [   81.795497] Bluetooth: HCI device and connection manager initialized
Apr 28 10:24:53 lv-426 kernel: [   81.795501] Bluetooth: HCI socket layer initialized
Apr 28 10:24:53 lv-426 kernel: [   81.826883] Bluetooth: L2CAP ver 2.8
Apr 28 10:24:53 lv-426 kernel: [   81.826887] Bluetooth: L2CAP socket layer initialized
Apr 28 10:24:53 lv-426 kernel: [   81.829580] Bluetooth: RFCOMM socket layer initialized
Apr 28 10:24:53 lv-426 kernel: [   81.829710] Bluetooth: RFCOMM TTY layer initialized
Apr 28 10:24:53 lv-426 kernel: [   81.829713] Bluetooth: RFCOMM ver 1.8
Apr 28 10:24:53 lv-426 kernel: [   46.788000] Time: acpi_pm clocksource has been installed.
Apr 28 10:24:54 lv-426 dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Apr 28 10:24:54 lv-426 dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 
Apr 28 10:24:54 lv-426 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Apr 28 10:24:54 lv-426 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Apr 28 10:25:21 lv-426 gconfd (frank-5703): starting (version 2.18.0.1), pid 5703 user 'frank'
Apr 28 10:25:21 lv-426 gconfd (frank-5703): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr 28 10:25:21 lv-426 gconfd (frank-5703): Resolved address "xml:readwrite:/home/frank/.gconf" to a writable configuration source at position 1
Apr 28 10:25:21 lv-426 gconfd (frank-5703): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr 28 10:25:21 lv-426 gconfd (frank-5703): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr 28 10:25:21 lv-426 gconfd (frank-5703): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr 28 10:25:29 lv-426 gconfd (frank-5703): Resolved address "xml:readwrite:/home/frank/.gconf" to a writable configuration source at position 0
Apr 28 10:36:05 lv-426 syslogd 1.4.1#20ubuntu4: restart.

```

Thanks,
rustikus

---

