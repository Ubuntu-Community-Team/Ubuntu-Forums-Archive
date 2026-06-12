---
title: "nvidia 6600 issues"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by siucdude on 2007-05-01
Hello, 
Maybe someone can help me, and I thank you in advance.

I am running Feisty, with all updates,  But since Edgy I have never been very successful running Nvidia, I have always ran the nv with bad resolution,

This morning my vacation started so i figured well let me try to fix this, 

I ran the reconfigure xorg and went through the steps but when it asked for autodetaction of screen, it goes blank and I can't do anything,  My processor goes very fast and my fans turn on but nothing,

I boot ok with nv but I don't get the right resolution,  I have reinstalled all nvidia packages and I am not on legacy yet.  

Its a laptop with 17 widescreen, and it ran fine in Edgy.  Even when I run the live cd it works ok but then goes bad after install. Also when I reinstall using the alternate cd and boot but all I get is a blank screen upon my boot right before the login screen after the splash, 
I did try all options to change, but if anyone had issues like this or knows what to do, let me know.

Thanks again

TJ

---

### Post by Ppeter on 2007-05-01
HI,

Can you post (attach) the:
Laptop type (incl. graphic card)
Your failing xorg.conf
And Xorg.0.log

\Peter

---

### Post by siucdude on 2007-05-02
Ok the Laptop is a Toshiba G25-AV513
the card is a nVidia NV43 GeForce Go 6600
My xorg.conf file is the same for failing as working I just change the nv to nvidia to make it fail. 
and my Xorg.0.log has two active 

Will post in next

---

### Post by siucdude on 2007-05-02
This is the files,

Xorg.0.log

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux tomasz-laptop 2.6.22-1-generic #1 SMP Mon Apr 30 10:49:22 GMT 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May  2 20:15:11 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV43 [GeForce Go 6600]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
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
(II) PCI: 00:00:0: chip 8086,2590 card 1179,0001 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2591 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1179,0001 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1179,0001 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1179,0001 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1179,0001 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1179,0001 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d3 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 1179,0253 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1e:3: chip 8086,266d card 1179,0001 rev 03 class 07,03,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2641 card 1179,0001 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1179,0001 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2653 card 1179,0f10 rev 03 class 01,06,01 hdr 00
(II) PCI: 01:00:0: chip 10de,0148 card 1179,0001 rev a2 class 03,00,00 hdr 00
(II) PCI: 04:05:0: chip 8086,4223 card 8086,1040 rev 05 class 02,80,00 hdr 00
(II) PCI: 04:08:0: chip 8086,1068 card 1179,0001 rev 03 class 02,00,00 hdr 00
(II) PCI: 04:09:0: chip 4444,0016 card 1179,0001 rev 01 class 04,00,00 hdr 00
(II) PCI: 04:0b:0: chip 104c,8031 card a000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 04:0b:2: chip 104c,8032 card 1179,0001 rev 00 class 0c,00,10 hdr 80
(II) PCI: 04:0b:3: chip 104c,8033 card 1179,0001 rev 00 class 01,80,00 hdr 80
(II) PCI: 04:0b:4: chip 104c,8034 card 1179,0001 rev 00 class 08,05,01 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xce000000 - 0xcfffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xcde00000 - 0xcdffffff (0x200000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xafe00000 - 0xafffffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,6), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xcdd00000 - 0xcddfffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x57ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (4:11:0), (4,5,5), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x54000000 - 0x57ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV43 [GeForce Go 6600] rev 162, Mem @ 0xcf000000/24, 0xb0000000/28, 0xce000000/24
(--) PCI: (4:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0x50000000/26
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
	[0] -1	0	0xcdd07a00 - 0xcdd07aff (0x100) MX[B]
	[1] -1	0	0xcdd07900 - 0xcdd079ff (0x100) MX[B]
	[2] -1	0	0xcdd07800 - 0xcdd078ff (0x100) MX[B]
	[3] -1	0	0xcdd04000 - 0xcdd05fff (0x2000) MX[B]
	[4] -1	0	0xcdd00000 - 0xcdd03fff (0x4000) MX[B]
	[5] -1	0	0xcdd07000 - 0xcdd077ff (0x800) MX[B]
	[6] -1	0	0xcddfe000 - 0xcddfefff (0x1000) MX[B]
	[7] -1	0	0xcddff000 - 0xcddfffff (0x1000) MX[B]
	[8] -1	0	0xcdcffc00 - 0xcdcfffff (0x400) MX[B]
	[9] -1	0	0x58000600 - 0x580006ff (0x100) MX[B]
	[10] -1	0	0x58000400 - 0x580005ff (0x200) MX[B]
	[11] -1	0	0x58000000 - 0x580003ff (0x400) MX[B]
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xcf000000 - 0xcfffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000af40 - 0x0000af7f (0x40) IX[B]
	[16] -1	0	0x00009f70 - 0x00009f7f (0x10) IX[B]
	[17] -1	0	0x00009f84 - 0x00009f87 (0x4) IX[B]
	[18] -1	0	0x00009f88 - 0x00009f8f (0x8) IX[B]
	[19] -1	0	0x00009f94 - 0x00009f97 (0x4) IX[B]
	[20] -1	0	0x00009f98 - 0x00009f9f (0x8) IX[B]
	[21] -1	0	0x00009fa0 - 0x00009faf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[27] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[28] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[29] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[30] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[31] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[32] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[33] -1	0	0x0000bfe0 - 0x0000bfff (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcdd07a00 - 0xcdd07aff (0x100) MX[B]
	[1] -1	0	0xcdd07900 - 0xcdd079ff (0x100) MX[B]
	[2] -1	0	0xcdd07800 - 0xcdd078ff (0x100) MX[B]
	[3] -1	0	0xcdd04000 - 0xcdd05fff (0x2000) MX[B]
	[4] -1	0	0xcdd00000 - 0xcdd03fff (0x4000) MX[B]
	[5] -1	0	0xcdd07000 - 0xcdd077ff (0x800) MX[B]
	[6] -1	0	0xcddfe000 - 0xcddfefff (0x1000) MX[B]
	[7] -1	0	0xcddff000 - 0xcddfffff (0x1000) MX[B]
	[8] -1	0	0xcdcffc00 - 0xcdcfffff (0x400) MX[B]
	[9] -1	0	0x58000600 - 0x580006ff (0x100) MX[B]
	[10] -1	0	0x58000400 - 0x580005ff (0x200) MX[B]
	[11] -1	0	0x58000000 - 0x580003ff (0x400) MX[B]
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xcf000000 - 0xcfffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000af40 - 0x0000af7f (0x40) IX[B]
	[16] -1	0	0x00009f70 - 0x00009f7f (0x10) IX[B]
	[17] -1	0	0x00009f84 - 0x00009f87 (0x4) IX[B]
	[18] -1	0	0x00009f88 - 0x00009f8f (0x8) IX[B]
	[19] -1	0	0x00009f94 - 0x00009f97 (0x4) IX[B]
	[20] -1	0	0x00009f98 - 0x00009f9f (0x8) IX[B]
	[21] -1	0	0x00009fa0 - 0x00009faf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[27] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[28] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[29] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[30] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[31] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[32] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[33] -1	0	0x0000bfe0 - 0x0000bfff (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B](B)
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
	[4] -1	0	0xcdd07a00 - 0xcdd07aff (0x100) MX[B]
	[5] -1	0	0xcdd07900 - 0xcdd079ff (0x100) MX[B]
	[6] -1	0	0xcdd07800 - 0xcdd078ff (0x100) MX[B]
	[7] -1	0	0xcdd04000 - 0xcdd05fff (0x2000) MX[B]
	[8] -1	0	0xcdd00000 - 0xcdd03fff (0x4000) MX[B]
	[9] -1	0	0xcdd07000 - 0xcdd077ff (0x800) MX[B]
	[10] -1	0	0xcddfe000 - 0xcddfefff (0x1000) MX[B]
	[11] -1	0	0xcddff000 - 0xcddfffff (0x1000) MX[B]
	[12] -1	0	0xcdcffc00 - 0xcdcfffff (0x400) MX[B]
	[13] -1	0	0x58000600 - 0x580006ff (0x100) MX[B]
	[14] -1	0	0x58000400 - 0x580005ff (0x200) MX[B]
	[15] -1	0	0x58000000 - 0x580003ff (0x400) MX[B]
	[16] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[17] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xcf000000 - 0xcfffffff (0x1000000) MX[B](B)
	[19] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000af40 - 0x0000af7f (0x40) IX[B]
	[23] -1	0	0x00009f70 - 0x00009f7f (0x10) IX[B]
	[24] -1	0	0x00009f84 - 0x00009f87 (0x4) IX[B]
	[25] -1	0	0x00009f88 - 0x00009f8f (0x8) IX[B]
	[26] -1	0	0x00009f94 - 0x00009f97 (0x4) IX[B]
	[27] -1	0	0x00009f98 - 0x00009f9f (0x8) IX[B]
	[28] -1	0	0x00009fa0 - 0x00009faf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[34] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[35] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[36] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[37] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[38] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[39] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[40] -1	0	0x0000bfe0 - 0x0000bfff (0x20) IX[B]
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
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
	[4] -1	0	0xcdd07a00 - 0xcdd07aff (0x100) MX[B]
	[5] -1	0	0xcdd07900 - 0xcdd079ff (0x100) MX[B]
	[6] -1	0	0xcdd07800 - 0xcdd078ff (0x100) MX[B]
	[7] -1	0	0xcdd04000 - 0xcdd05fff (0x2000) MX[B]
	[8] -1	0	0xcdd00000 - 0xcdd03fff (0x4000) MX[B]
	[9] -1	0	0xcdd07000 - 0xcdd077ff (0x800) MX[B]
	[10] -1	0	0xcddfe000 - 0xcddfefff (0x1000) MX[B]
	[11] -1	0	0xcddff000 - 0xcddfffff (0x1000) MX[B]
	[12] -1	0	0xcdcffc00 - 0xcdcfffff (0x400) MX[B]
	[13] -1	0	0x58000600 - 0x580006ff (0x100) MX[B]
	[14] -1	0	0x58000400 - 0x580005ff (0x200) MX[B]
	[15] -1	0	0x58000000 - 0x580003ff (0x400) MX[B]
	[16] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[17] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xcf000000 - 0xcfffffff (0x1000000) MX[B](B)
	[19] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000af40 - 0x0000af7f (0x40) IX[B]
	[23] -1	0	0x00009f70 - 0x00009f7f (0x10) IX[B]
	[24] -1	0	0x00009f84 - 0x00009f87 (0x4) IX[B]
	[25] -1	0	0x00009f88 - 0x00009f8f (0x8) IX[B]
	[26] -1	0	0x00009f94 - 0x00009f97 (0x4) IX[B]
	[27] -1	0	0x00009f98 - 0x00009f9f (0x8) IX[B]
	[28] -1	0	0x00009fa0 - 0x00009faf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[34] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[35] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[36] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[37] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[38] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[39] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[40] -1	0	0x0000bfe0 - 0x0000bfff (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcdd07a00 - 0xcdd07aff (0x100) MX[B]
	[5] -1	0	0xcdd07900 - 0xcdd079ff (0x100) MX[B]
	[6] -1	0	0xcdd07800 - 0xcdd078ff (0x100) MX[B]
	[7] -1	0	0xcdd04000 - 0xcdd05fff (0x2000) MX[B]
	[8] -1	0	0xcdd00000 - 0xcdd03fff (0x4000) MX[B]
	[9] -1	0	0xcdd07000 - 0xcdd077ff (0x800) MX[B]
	[10] -1	0	0xcddfe000 - 0xcddfefff (0x1000) MX[B]
	[11] -1	0	0xcddff000 - 0xcddfffff (0x1000) MX[B]
	[12] -1	0	0xcdcffc00 - 0xcdcfffff (0x400) MX[B]
	[13] -1	0	0x58000600 - 0x580006ff (0x100) MX[B]
	[14] -1	0	0x58000400 - 0x580005ff (0x200) MX[B]
	[15] -1	0	0x58000000 - 0x580003ff (0x400) MX[B]
	[16] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[17] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xcf000000 - 0xcfffffff (0x1000000) MX[B](B)
	[19] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000af40 - 0x0000af7f (0x40) IX[B]
	[26] -1	0	0x00009f70 - 0x00009f7f (0x10) IX[B]
	[27] -1	0	0x00009f84 - 0x00009f87 (0x4) IX[B]
	[28] -1	0	0x00009f88 - 0x00009f8f (0x8) IX[B]
	[29] -1	0	0x00009f94 - 0x00009f97 (0x4) IX[B]
	[30] -1	0	0x00009f98 - 0x00009f9f (0x8) IX[B]
	[31] -1	0	0x00009fa0 - 0x00009faf (0x10) IX[B]
	[32] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[33] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[34] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[37] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[38] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[39] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[40] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[41] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[42] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[43] -1	0	0x0000bfe0 - 0x0000bfff (0x20) IX[B]
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "UseEDID" "False"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Option "ModeValidation" "DFP-0: AllowNon60HzDFPModes, NoEdidModes, NoVesaModes, NoXServerModes, NoDFPNativeResolutionCheck"
(**) NVIDIA(0): Option "DynamicTwinView" "false"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
```

---

### Post by siucdude on 2007-05-02
Xorg.conf file,

Just remember this is a very costumized file, I can restore my back up that is plain and simple and try dpkg-reconfigure but nothing, it's like

The system freezes when it tries the Nvidia driver.

Thanks

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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce Go 6600]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option          "UseEDID" "False"
	Option		"AddARGBVisuals""True"
	Option		"AddARGBGLXVisuals""True"
	Option		"NoLogo""True"
	Option		"DynamicTwinView""false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
	Modeline 	"1440x900" 134.52 1440 1536 1688 1936 900 901 904 939
	Modeline 	"1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce Go 6600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	Option         "ModeValidation" "DFP-0: AllowNon60HzDFPModes, NoEdidModes, NoVesaModes, NoXServerModes, NoDFPNativeResolutionCheck"
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by augegr on 2007-05-03
Try changing this:
```
Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce Go 6600]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option          "UseEDID" "False"
	Option		"AddARGBVisuals""True"
	Option		"AddARGBGLXVisuals""True"
	Option		"NoLogo""True"
	Option		"DynamicTwinView""false"
EndSection

```

to this:

```

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce Go 6600]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"AddARGBGLXVisuals""True"
	Option		"NoLogo""True"
EndSection

```

Also put a # infront of this line:
```

Option         "ModeValidation" "DFP-0: AllowNon60HzDFPModes, NoEdidModes, NoVesaModes, NoXServerModes, NoDFPNativeResolutionCheck"

```
Make sure you have installed linux restricted modules, the appropriate version for your kernel that is.

---

### Post by siucdude on 2007-05-03
thanks for the reply, but nothing,

well first I have everything installed right,  My Xorg does not provide the typical error,  It looks to be something else. because in the past I have always been able to press CTRL+ALT+F* and this time I can't do anything, but pressing CTRL+ALT+DEL which reboots, (so the keyboard is not locked)  

Plus the option ModeValidation is designed to work for my resolution 1440*900 under  "nv" 

I don't care what resolution I get, I can get that fixed but I just want to boot nvidia driver.

Thanks for your help and anyone else that is willing to look at it.

TJ

---

### Post by siucdude on 2007-05-21
anyone else,

---

### Post by orrorin on 2007-05-22
try this forum as well ...

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

