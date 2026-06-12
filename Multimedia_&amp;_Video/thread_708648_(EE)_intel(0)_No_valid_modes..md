---
title: "(EE) intel(0): No valid modes."
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by jrgns on 2008-02-26
I'm trying to get my system to use the intel driver for the onboard Graphics driver
```

$ lspci | grep Graphic

00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

```
```

$ cat /etc/X11/xorg.conf

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Intel Corporation Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "VM7E"
        Option          "DPMS"
        HorizSync       30-100
        VertRefresh     50-100
        ModeLine "1024x768"   44.9 1024 1032 1208 1264    768  768  776  817 +hsync +vsync Interlace
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Integrated Graphics Controller"
        Monitor         "VM7E"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "DRI"
        Mode    0666
EndSection

```
```

$ cat /var/log/X


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux narnia 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 27 00:33:35 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "VM7E"
(**) |   |-->Device "Intel Corporation Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29c0 card 8086,5044 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,29c2 card 8086,5044 rev 02 class 03,00,00 hdr 00
(II) PCI: 00:03:0: chip 8086,29c4 card 8086,5044 rev 02 class 07,80,00 hdr 80
(II) PCI: 00:19:0: chip 8086,294c card 8086,0001 rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2937 card 8086,5044 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 8086,5044 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 8086,5044 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 8086,5044 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2942 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,2944 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2946 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 8086,5044 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 8086,5044 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 8086,5044 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 8086,5044 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2912 card 8086,5044 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2920 card 8086,5044 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 8086,5044 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 8086,5044 rev 02 class 01,01,85 hdr 00
(II) PCI: 02:00:0: chip 11ab,6101 card 11ab,6101 rev b1 class 01,01,8f hdr 00
(II) PCI: 06:00:0: chip 1102,0002 card 1102,8061 rev 07 class 04,01,00 hdr 80
(II) PCI: 06:00:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 06:01:0: chip 1814,0201 card 1458,e932 rev 01 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x90400000 - 0x904fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:1), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x90100000 - 0x901fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:2), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0x90500000 - 0x905fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:3), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x90600000 - 0x906fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:4), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0x90700000 - 0x907fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x90000000 - 0x900fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Integrated Graphics Controller rev 2, Mem @ 0x90300000/19, 0x80000000/28, 0x90200000/20, I/O @ 0x3160/3
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
	[0] -1	0	0x90000000 - 0x90001fff (0x2000) MX[B]
	[1] -1	0	0x90100000 - 0x901001ff (0x200) MX[B]
	[2] -1	0	0x903a1800 - 0x903a18ff (0x100) MX[B]
	[3] -1	0	0x903a1000 - 0x903a13ff (0x400) MX[B]
	[4] -1	0	0x903a1400 - 0x903a17ff (0x400) MX[B]
	[5] -1	0	0x903a0000 - 0x903a0fff (0x1000) MX[B]
	[6] -1	0	0x90380000 - 0x9039ffff (0x20000) MX[B]
	[7] -1	0	0x903a1900 - 0x903a190f (0x10) MX[B]
	[8] -1	0	0x90200000 - 0x902fffff (0x100000) MX[B](B)
	[9] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[11] -1	0	0x00001020 - 0x00001027 (0x8) IX[B]
	[12] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[13] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[14] -1	0	0x00002020 - 0x00002023 (0x4) IX[B]
	[15] -1	0	0x00002010 - 0x00002017 (0x8) IX[B]
	[16] -1	0	0x00002024 - 0x00002027 (0x4) IX[B]
	[17] -1	0	0x00002018 - 0x0000201f (0x8) IX[B]
	[18] -1	0	0x00003100 - 0x0000310f (0x10) IX[B]
	[19] -1	0	0x00003110 - 0x0000311f (0x10) IX[B]
	[20] -1	0	0x00003168 - 0x0000316b (0x4) IX[B]
	[21] -1	0	0x00003140 - 0x00003147 (0x8) IX[B]
	[22] -1	0	0x0000316c - 0x0000316f (0x4) IX[B]
	[23] -1	0	0x00003148 - 0x0000314f (0x8) IX[B]
	[24] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[25] -1	0	0x00003120 - 0x0000312f (0x10) IX[B]
	[26] -1	0	0x00003130 - 0x0000313f (0x10) IX[B]
	[27] -1	0	0x00003170 - 0x00003173 (0x4) IX[B]
	[28] -1	0	0x00003150 - 0x00003157 (0x8) IX[B]
	[29] -1	0	0x00003174 - 0x00003177 (0x4) IX[B]
	[30] -1	0	0x00003158 - 0x0000315f (0x8) IX[B]
	[31] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[32] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[33] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[34] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[35] -1	0	0x000030a0 - 0x000030bf (0x20) IX[B]
	[36] -1	0	0x000030c0 - 0x000030df (0x20) IX[B]
	[37] -1	0	0x000030e0 - 0x000030ff (0x20) IX[B]
	[38] -1	0	0x00003160 - 0x00003167 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x90000000 - 0x90001fff (0x2000) MX[B]
	[1] -1	0	0x90100000 - 0x901001ff (0x200) MX[B]
	[2] -1	0	0x903a1800 - 0x903a18ff (0x100) MX[B]
	[3] -1	0	0x903a1000 - 0x903a13ff (0x400) MX[B]
	[4] -1	0	0x903a1400 - 0x903a17ff (0x400) MX[B]
	[5] -1	0	0x903a0000 - 0x903a0fff (0x1000) MX[B]
	[6] -1	0	0x90380000 - 0x9039ffff (0x20000) MX[B]
	[7] -1	0	0x903a1900 - 0x903a190f (0x10) MX[B]
	[8] -1	0	0x90200000 - 0x902fffff (0x100000) MX[B](B)
	[9] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[10] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[11] -1	0	0x00001020 - 0x00001027 (0x8) IX[B]
	[12] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[13] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[14] -1	0	0x00002020 - 0x00002023 (0x4) IX[B]
	[15] -1	0	0x00002010 - 0x00002017 (0x8) IX[B]
	[16] -1	0	0x00002024 - 0x00002027 (0x4) IX[B]
	[17] -1	0	0x00002018 - 0x0000201f (0x8) IX[B]
	[18] -1	0	0x00003100 - 0x0000310f (0x10) IX[B]
	[19] -1	0	0x00003110 - 0x0000311f (0x10) IX[B]
	[20] -1	0	0x00003168 - 0x0000316b (0x4) IX[B]
	[21] -1	0	0x00003140 - 0x00003147 (0x8) IX[B]
	[22] -1	0	0x0000316c - 0x0000316f (0x4) IX[B]
	[23] -1	0	0x00003148 - 0x0000314f (0x8) IX[B]
	[24] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[25] -1	0	0x00003120 - 0x0000312f (0x10) IX[B]
	[26] -1	0	0x00003130 - 0x0000313f (0x10) IX[B]
	[27] -1	0	0x00003170 - 0x00003173 (0x4) IX[B]
	[28] -1	0	0x00003150 - 0x00003157 (0x8) IX[B]
	[29] -1	0	0x00003174 - 0x00003177 (0x4) IX[B]
	[30] -1	0	0x00003158 - 0x0000315f (0x8) IX[B]
	[31] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[32] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[33] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[34] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[35] -1	0	0x000030a0 - 0x000030bf (0x20) IX[B]
	[36] -1	0	0x000030c0 - 0x000030df (0x20) IX[B]
	[37] -1	0	0x000030e0 - 0x000030ff (0x20) IX[B]
	[38] -1	0	0x00003160 - 0x00003167 (0x8) IX[B](B)
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
	[4] -1	0	0x90000000 - 0x90001fff (0x2000) MX[B]
	[5] -1	0	0x90100000 - 0x901001ff (0x200) MX[B]
	[6] -1	0	0x903a1800 - 0x903a18ff (0x100) MX[B]
	[7] -1	0	0x903a1000 - 0x903a13ff (0x400) MX[B]
	[8] -1	0	0x903a1400 - 0x903a17ff (0x400) MX[B]
	[9] -1	0	0x903a0000 - 0x903a0fff (0x1000) MX[B]
	[10] -1	0	0x90380000 - 0x9039ffff (0x20000) MX[B]
	[11] -1	0	0x903a1900 - 0x903a190f (0x10) MX[B]
	[12] -1	0	0x90200000 - 0x902fffff (0x100000) MX[B](B)
	[13] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[14] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00001020 - 0x00001027 (0x8) IX[B]
	[18] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[19] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[20] -1	0	0x00002020 - 0x00002023 (0x4) IX[B]
	[21] -1	0	0x00002010 - 0x00002017 (0x8) IX[B]
	[22] -1	0	0x00002024 - 0x00002027 (0x4) IX[B]
	[23] -1	0	0x00002018 - 0x0000201f (0x8) IX[B]
	[24] -1	0	0x00003100 - 0x0000310f (0x10) IX[B]
	[25] -1	0	0x00003110 - 0x0000311f (0x10) IX[B]
	[26] -1	0	0x00003168 - 0x0000316b (0x4) IX[B]
	[27] -1	0	0x00003140 - 0x00003147 (0x8) IX[B]
	[28] -1	0	0x0000316c - 0x0000316f (0x4) IX[B]
	[29] -1	0	0x00003148 - 0x0000314f (0x8) IX[B]
	[30] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[31] -1	0	0x00003120 - 0x0000312f (0x10) IX[B]
	[32] -1	0	0x00003130 - 0x0000313f (0x10) IX[B]
	[33] -1	0	0x00003170 - 0x00003173 (0x4) IX[B]
	[34] -1	0	0x00003150 - 0x00003157 (0x8) IX[B]
	[35] -1	0	0x00003174 - 0x00003177 (0x4) IX[B]
	[36] -1	0	0x00003158 - 0x0000315f (0x8) IX[B]
	[37] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[38] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[39] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[40] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[41] -1	0	0x000030a0 - 0x000030bf (0x20) IX[B]
	[42] -1	0	0x000030c0 - 0x000030df (0x20) IX[B]
	[43] -1	0	0x000030e0 - 0x000030ff (0x20) IX[B]
	[44] -1	0	0x00003160 - 0x00003167 (0x8) IX[B](B)
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
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
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, 965G, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(--) Chipset G33 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90001fff (0x2000) MX[B]
	[5] -1	0	0x90100000 - 0x901001ff (0x200) MX[B]
	[6] -1	0	0x903a1800 - 0x903a18ff (0x100) MX[B]
	[7] -1	0	0x903a1000 - 0x903a13ff (0x400) MX[B]
	[8] -1	0	0x903a1400 - 0x903a17ff (0x400) MX[B]
	[9] -1	0	0x903a0000 - 0x903a0fff (0x1000) MX[B]
	[10] -1	0	0x90380000 - 0x9039ffff (0x20000) MX[B]
	[11] -1	0	0x903a1900 - 0x903a190f (0x10) MX[B]
	[12] -1	0	0x90200000 - 0x902fffff (0x100000) MX[B](B)
	[13] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[14] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00001020 - 0x00001027 (0x8) IX[B]
	[18] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[19] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[20] -1	0	0x00002020 - 0x00002023 (0x4) IX[B]
	[21] -1	0	0x00002010 - 0x00002017 (0x8) IX[B]
	[22] -1	0	0x00002024 - 0x00002027 (0x4) IX[B]
	[23] -1	0	0x00002018 - 0x0000201f (0x8) IX[B]
	[24] -1	0	0x00003100 - 0x0000310f (0x10) IX[B]
	[25] -1	0	0x00003110 - 0x0000311f (0x10) IX[B]
	[26] -1	0	0x00003168 - 0x0000316b (0x4) IX[B]
	[27] -1	0	0x00003140 - 0x00003147 (0x8) IX[B]
	[28] -1	0	0x0000316c - 0x0000316f (0x4) IX[B]
	[29] -1	0	0x00003148 - 0x0000314f (0x8) IX[B]
	[30] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[31] -1	0	0x00003120 - 0x0000312f (0x10) IX[B]
	[32] -1	0	0x00003130 - 0x0000313f (0x10) IX[B]
	[33] -1	0	0x00003170 - 0x00003173 (0x4) IX[B]
	[34] -1	0	0x00003150 - 0x00003157 (0x8) IX[B]
	[35] -1	0	0x00003174 - 0x00003177 (0x4) IX[B]
	[36] -1	0	0x00003158 - 0x0000315f (0x8) IX[B]
	[37] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[38] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[39] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[40] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[41] -1	0	0x000030a0 - 0x000030bf (0x20) IX[B]
	[42] -1	0	0x000030c0 - 0x000030df (0x20) IX[B]
	[43] -1	0	0x000030e0 - 0x000030ff (0x20) IX[B]
	[44] -1	0	0x00003160 - 0x00003167 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x90000000 - 0x90001fff (0x2000) MX[B]
	[5] -1	0	0x90100000 - 0x901001ff (0x200) MX[B]
	[6] -1	0	0x903a1800 - 0x903a18ff (0x100) MX[B]
	[7] -1	0	0x903a1000 - 0x903a13ff (0x400) MX[B]
	[8] -1	0	0x903a1400 - 0x903a17ff (0x400) MX[B]
	[9] -1	0	0x903a0000 - 0x903a0fff (0x1000) MX[B]
	[10] -1	0	0x90380000 - 0x9039ffff (0x20000) MX[B]
	[11] -1	0	0x903a1900 - 0x903a190f (0x10) MX[B]
	[12] -1	0	0x90200000 - 0x902fffff (0x100000) MX[B](B)
	[13] -1	0	0x80000000 - 0x8fffffff (0x10000000) MX[B](B)
	[14] -1	0	0x90300000 - 0x9037ffff (0x80000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001020 - 0x00001027 (0x8) IX[B]
	[21] -1	0	0x00001000 - 0x0000101f (0x20) IX[B]
	[22] -1	0	0x00002000 - 0x0000200f (0x10) IX[B]
	[23] -1	0	0x00002020 - 0x00002023 (0x4) IX[B]
	[24] -1	0	0x00002010 - 0x00002017 (0x8) IX[B]
	[25] -1	0	0x00002024 - 0x00002027 (0x4) IX[B]
	[26] -1	0	0x00002018 - 0x0000201f (0x8) IX[B]
	[27] -1	0	0x00003100 - 0x0000310f (0x10) IX[B]
	[28] -1	0	0x00003110 - 0x0000311f (0x10) IX[B]
	[29] -1	0	0x00003168 - 0x0000316b (0x4) IX[B]
	[30] -1	0	0x00003140 - 0x00003147 (0x8) IX[B]
	[31] -1	0	0x0000316c - 0x0000316f (0x4) IX[B]
	[32] -1	0	0x00003148 - 0x0000314f (0x8) IX[B]
	[33] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[34] -1	0	0x00003120 - 0x0000312f (0x10) IX[B]
	[35] -1	0	0x00003130 - 0x0000313f (0x10) IX[B]
	[36] -1	0	0x00003170 - 0x00003173 (0x4) IX[B]
	[37] -1	0	0x00003150 - 0x00003157 (0x8) IX[B]
	[38] -1	0	0x00003174 - 0x00003177 (0x4) IX[B]
	[39] -1	0	0x00003158 - 0x0000315f (0x8) IX[B]
	[40] -1	0	0x00003020 - 0x0000303f (0x20) IX[B]
	[41] -1	0	0x00003040 - 0x0000305f (0x20) IX[B]
	[42] -1	0	0x00003060 - 0x0000307f (0x20) IX[B]
	[43] -1	0	0x00003080 - 0x0000309f (0x20) IX[B]
	[44] -1	0	0x000030a0 - 0x000030bf (0x20) IX[B]
	[45] -1	0	0x000030c0 - 0x000030df (0x20) IX[B]
	[46] -1	0	0x000030e0 - 0x000030ff (0x20) IX[B]
	[47] -1	0	0x00003160 - 0x00003167 (0x8) IX[B](B)
	[48] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[49] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G33
(--) intel(0): Chipset: "G33"
(--) intel(0): Linear framebuffer at 0x80000000
(--) intel(0): IO registers at addr 0x90300000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) intel(0): Output VGA using monitor section VM7E
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
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output VGA disconnected
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

I tried playing around with the HorizSync, VertRefresh and ModeLine, but with no success. When I remove the config file, Xorg works fine, but with the vesa driver. Not what I want... I also tried using the i810 driver, but no luck.

Any advice?

---

