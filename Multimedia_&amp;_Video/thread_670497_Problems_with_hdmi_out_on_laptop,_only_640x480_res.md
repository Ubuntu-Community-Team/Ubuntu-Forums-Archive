---
title: "Problems with hdmi out on laptop, only 640x480 res"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by TorjusH on 2008-01-17
Hiya!

I've been using ubuntu for a while, and i love it :) But now i have come across a problem, and i really can't figure out how to solve it. For a while i have been using a svideo-cable to connect my laptop to my tv, and it has been working fine all along. But now i bought an hdmi-cable to connect my laptop to my tv, and its not working. It seems like it doesnt send any higher resolution than 640x480.

Using nvidia-settings i can't select any resolutions higher than 640x480, even though both the cable and my tv supports it. The tv is hd720p. I have tried messing around with xorg.conf, but i am pretty clueless about what to do. I have some different things i have found on various forums, but nothing really helps.

Anyone know how to solve this?

Heres the output of xorg.0.log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux torjus-ubuntu 2.6.22-14-generic #1 SMP Tue Dec 18 05:28:27 UTC 2007 x86_64
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 17 20:38:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "Xinerama" "0"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7cd8a0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2a00 card 103c,30cc rev 0c class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2a01 card 0000,0000 rev 0c class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 103c,30cc rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 103c,30cc rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 103c,30cc rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 103c,30cc rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,2849 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 103c,30cc rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 103c,30cc rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 103c,30cc rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 103c,30cc rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2815 card 103c,30cc rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card 103c,30cc rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2829 card 103c,30cc rev 03 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 103c,30cc rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0425 card 103c,30cc rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 8086,4229 card 8086,1101 rev 61 class 02,80,00 hdr 00
(II) PCI: 06:00:0: chip 10ec,8168 card 103c,30cc rev 01 class 02,00,00 hdr 00
(II) PCI: 07:09:0: chip 1180,0832 card 103c,30cc rev 05 class 0c,00,10 hdr 80
(II) PCI: 07:09:1: chip 1180,0822 card 103c,30cc rev 22 class 08,05,00 hdr 80
(II) PCI: 07:09:2: chip 1180,0843 card 103c,30cc rev 12 class 08,80,00 hdr 80
(II) PCI: 07:09:3: chip 1180,0592 card 103c,30cc rev 12 class 08,80,00 hdr 80
(II) PCI: 07:09:4: chip 1180,0852 card 103c,30cc rev 12 class 08,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xcc000000 - 0xceffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xf80fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:1), (0,4,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf3ffffff (0x4000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:28:5), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xf8100000 - 0xf81fffff (0x100000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:30:0), (0,7,7), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xf8200000 - 0xf82fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0425) rev 161, Mem @ 0xce000000/24, 0xd0000000/28, 0xcc000000/25, I/O @ 0x2000/7
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
(II) Active PCI resource ranges:
	[0] -1	0	0xf8201400 - 0xf82014ff (0x100) MX[B]
	[1] -1	0	0xf8201000 - 0xf82010ff (0x100) MX[B]
	[2] -1	0	0xf8200c00 - 0xf8200cff (0x100) MX[B]
	[3] -1	0	0xf8200800 - 0xf82008ff (0x100) MX[B]
	[4] -1	0	0xf8200000 - 0xf82007ff (0x800) MX[B]
	[5] -1	0	0xf8100000 - 0xf8100fff (0x1000) MX[B]
	[6] -1	0	0xf8000000 - 0xf8001fff (0x2000) MX[B]
	[7] -1	0	0x88100000 - 0x881000ff (0x100) MX[B]
	[8] -1	0	0xf8504000 - 0xf85047ff (0x800) MX[B]
	[9] -1	0	0xf8504c00 - 0xf8504fff (0x400) MX[B]
	[10] -1	0	0xf8500000 - 0xf8503fff (0x4000) MX[B]
	[11] -1	0	0xf8504800 - 0xf8504bff (0x400) MX[B]
	[12] -1	0	0xcc000000 - 0xcdffffff (0x2000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[15] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[16] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[17] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[18] -1	0	0x000018c8 - 0x000018cb (0x4) IX[B]
	[19] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[20] -1	0	0x000018cc - 0x000018cf (0x4) IX[B]
	[21] -1	0	0x000018d8 - 0x000018df (0x8) IX[B]
	[22] -1	0	0x000018a0 - 0x000018af (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[28] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8201400 - 0xf82014ff (0x100) MX[B]
	[1] -1	0	0xf8201000 - 0xf82010ff (0x100) MX[B]
	[2] -1	0	0xf8200c00 - 0xf8200cff (0x100) MX[B]
	[3] -1	0	0xf8200800 - 0xf82008ff (0x100) MX[B]
	[4] -1	0	0xf8200000 - 0xf82007ff (0x800) MX[B]
	[5] -1	0	0xf8100000 - 0xf8100fff (0x1000) MX[B]
	[6] -1	0	0xf8000000 - 0xf8001fff (0x2000) MX[B]
	[7] -1	0	0x88100000 - 0x881000ff (0x100) MX[B]
	[8] -1	0	0xf8504000 - 0xf85047ff (0x800) MX[B]
	[9] -1	0	0xf8504c00 - 0xf8504fff (0x400) MX[B]
	[10] -1	0	0xf8500000 - 0xf8503fff (0x4000) MX[B]
	[11] -1	0	0xf8504800 - 0xf8504bff (0x400) MX[B]
	[12] -1	0	0xcc000000 - 0xcdffffff (0x2000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[15] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[16] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[17] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[18] -1	0	0x000018c8 - 0x000018cb (0x4) IX[B]
	[19] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[20] -1	0	0x000018cc - 0x000018cf (0x4) IX[B]
	[21] -1	0	0x000018d8 - 0x000018df (0x8) IX[B]
	[22] -1	0	0x000018a0 - 0x000018af (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[28] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
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
	[4] -1	0	0xf8201400 - 0xf82014ff (0x100) MX[B]
	[5] -1	0	0xf8201000 - 0xf82010ff (0x100) MX[B]
	[6] -1	0	0xf8200c00 - 0xf8200cff (0x100) MX[B]
	[7] -1	0	0xf8200800 - 0xf82008ff (0x100) MX[B]
	[8] -1	0	0xf8200000 - 0xf82007ff (0x800) MX[B]
	[9] -1	0	0xf8100000 - 0xf8100fff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf8001fff (0x2000) MX[B]
	[11] -1	0	0x88100000 - 0x881000ff (0x100) MX[B]
	[12] -1	0	0xf8504000 - 0xf85047ff (0x800) MX[B]
	[13] -1	0	0xf8504c00 - 0xf8504fff (0x400) MX[B]
	[14] -1	0	0xf8500000 - 0xf8503fff (0x4000) MX[B]
	[15] -1	0	0xf8504800 - 0xf8504bff (0x400) MX[B]
	[16] -1	0	0xcc000000 - 0xcdffffff (0x2000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[23] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[24] -1	0	0x000018c8 - 0x000018cb (0x4) IX[B]
	[25] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[26] -1	0	0x000018cc - 0x000018cf (0x4) IX[B]
	[27] -1	0	0x000018d8 - 0x000018df (0x8) IX[B]
	[28] -1	0	0x000018a0 - 0x000018af (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[34] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[35] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[36] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[37] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[38] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:51:24 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:10:47 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8201400 - 0xf82014ff (0x100) MX[B]
	[5] -1	0	0xf8201000 - 0xf82010ff (0x100) MX[B]
	[6] -1	0	0xf8200c00 - 0xf8200cff (0x100) MX[B]
	[7] -1	0	0xf8200800 - 0xf82008ff (0x100) MX[B]
	[8] -1	0	0xf8200000 - 0xf82007ff (0x800) MX[B]
	[9] -1	0	0xf8100000 - 0xf8100fff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf8001fff (0x2000) MX[B]
	[11] -1	0	0x88100000 - 0x881000ff (0x100) MX[B]
	[12] -1	0	0xf8504000 - 0xf85047ff (0x800) MX[B]
	[13] -1	0	0xf8504c00 - 0xf8504fff (0x400) MX[B]
	[14] -1	0	0xf8500000 - 0xf8503fff (0x4000) MX[B]
	[15] -1	0	0xf8504800 - 0xf8504bff (0x400) MX[B]
	[16] -1	0	0xcc000000 - 0xcdffffff (0x2000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[23] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[24] -1	0	0x000018c8 - 0x000018cb (0x4) IX[B]
	[25] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[26] -1	0	0x000018cc - 0x000018cf (0x4) IX[B]
	[27] -1	0	0x000018d8 - 0x000018df (0x8) IX[B]
	[28] -1	0	0x000018a0 - 0x000018af (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[34] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[35] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[36] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[37] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[38] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8201400 - 0xf82014ff (0x100) MX[B]
	[5] -1	0	0xf8201000 - 0xf82010ff (0x100) MX[B]
	[6] -1	0	0xf8200c00 - 0xf8200cff (0x100) MX[B]
	[7] -1	0	0xf8200800 - 0xf82008ff (0x100) MX[B]
	[8] -1	0	0xf8200000 - 0xf82007ff (0x800) MX[B]
	[9] -1	0	0xf8100000 - 0xf8100fff (0x1000) MX[B]
	[10] -1	0	0xf8000000 - 0xf8001fff (0x2000) MX[B]
	[11] -1	0	0x88100000 - 0x881000ff (0x100) MX[B]
	[12] -1	0	0xf8504000 - 0xf85047ff (0x800) MX[B]
	[13] -1	0	0xf8504c00 - 0xf8504fff (0x400) MX[B]
	[14] -1	0	0xf8500000 - 0xf8503fff (0x4000) MX[B]
	[15] -1	0	0xf8504800 - 0xf8504bff (0x400) MX[B]
	[16] -1	0	0xcc000000 - 0xcdffffff (0x2000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[26] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[27] -1	0	0x000018c8 - 0x000018cb (0x4) IX[B]
	[28] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[29] -1	0	0x000018cc - 0x000018cf (0x4) IX[B]
	[30] -1	0	0x000018d8 - 0x000018df (0x8) IX[B]
	[31] -1	0	0x000018a0 - 0x000018af (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[37] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[38] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[39] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[40] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[41] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP: 1440x900 +0+0; DFP: 1024x768 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8600M GS (G86) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.44.00.15
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8600M GS at PCI:1:0:0:
(--) NVIDIA(0):     LPL (DFP-0)
(--) NVIDIA(0):     Tatung V32MCHK (DFP-1)
(--) NVIDIA(0): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): LPL (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(0): Tatung V32MCHK (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Tatung V32MCHK (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
(WW) NVIDIA(0): Multiple display devices requested "DFP-0, DFP-1" but TwinView
(WW) NVIDIA(0):     not enabled; this screen will only use display device
(WW) NVIDIA(0):     "DFP-0".
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP:1440x900+0+0"
(II) NVIDIA(0):     "DFP:1024x768+0+0"
(II) NVIDIA(0):     "DFP:800x600+0+0"
(II) NVIDIA(0):     "DFP:640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (98, 99); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) NVIDIA(1): Creating default Display subsection in Screen section
	"Screen1" for depth/fbbpp 24/32
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TVStandard" "HD720p"
(**) NVIDIA(1): Option "TVOutFormat" "COMPONENT"
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "1280x760"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing COMPONENT output
(**) NVIDIA(1): TV Standard string: "HD720p"
(II) NVIDIA(1): NVIDIA GPU GeForce 8600M GS (G86) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 60.86.44.00.15
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 8600M GS at PCI:1:0:0:
(--) NVIDIA(1):     LPL (DFP-0)
(--) NVIDIA(1):     Tatung V32MCHK (DFP-1)
(--) NVIDIA(1): LPL (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): LPL (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(1): Tatung V32MCHK (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(1): Tatung V32MCHK (DFP-1): Internal Single Link TMDS
(II) NVIDIA(1): Assigned Display Device: DFP-1
(WW) NVIDIA(1): No valid modes for "1280x760"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 640 x 480
(--) NVIDIA(1): DPI set to (23, 30); computed from "UseEdidDpi" X config
(--) NVIDIA(1):     option
(==) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xcc000000 - 0xcdffffff (0x2000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xce000000 - 0xceffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xf8201400 - 0xf82014ff (0x100) MX[B]
	[8] -1	0	0xf8201000 - 0xf82010ff (0x100) MX[B]
	[9] -1	0	0xf8200c00 - 0xf8200cff (0x100) MX[B]
	[10] -1	0	0xf8200800 - 0xf82008ff (0x100) MX[B]
	[11] -1	0	0xf8200000 - 0xf82007ff (0x800) MX[B]
	[12] -1	0	0xf8100000 - 0xf8100fff (0x1000) MX[B]
	[13] -1	0	0xf8000000 - 0xf8001fff (0x2000) MX[B]
	[14] -1	0	0x88100000 - 0x881000ff (0x100) MX[B]
	[15] -1	0	0xf8504000 - 0xf85047ff (0x800) MX[B]
	[16] -1	0	0xf8504c00 - 0xf8504fff (0x400) MX[B]
	[17] -1	0	0xf8500000 - 0xf8503fff (0x4000) MX[B]
	[18] -1	0	0xf8504800 - 0xf8504bff (0x400) MX[B]
	[19] -1	0	0xcc000000 - 0xcdffffff (0x2000000) MX[B](B)
	[20] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[21] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[25] 0	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[29] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[30] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[31] -1	0	0x000018c8 - 0x000018cb (0x4) IX[B]
	[32] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[33] -1	0	0x000018cc - 0x000018cf (0x4) IX[B]
	[34] -1	0	0x000018d8 - 0x000018df (0x8) IX[B]
	[35] -1	0	0x000018a0 - 0x000018af (0x10) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[41] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[42] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[43] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[44] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[45] -1	0	0x00002000 - 0x0000207f (0x80) IX[B](B)
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "DFP:1440x900+0+0"
(--) NVIDIA(0): No video decoder detected
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Initialized GART.
(WW) NVIDIA(1): Display change hotkeys not supported with multiple X screens.
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): Built-in logo is bigger than the screen.
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
(**) Option "XkbLayout" "no"
(**) Generic Keyboard: XkbLayout: "no"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
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
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
Atom 4, CARD32 4, unsigned long 8
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9
```

And here is my xorg.conf (yeah, its messy, i know :P)
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:53 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:17 PDT 2007
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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "dri"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    ModeLine "1280x760"    79.33  1280 1344 1480 1680  760 761 764 787  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GS"
    BusID          "PCI:1:0:0"
    Screen          1
Option          "MetaModes"    "1280x760"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1440x900 +0+0; DFP: 1024x768 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
        Option          "TVOutFormat" "COMPONENT"
        Option          "TVStandard" "HD720p"
EndSection
Section "Modes"
    Identifier "Custom modes"

EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I have messed around a bit with custom modelines, but don't really know how to do it...

Any help would be greatly appreciated :)

---

