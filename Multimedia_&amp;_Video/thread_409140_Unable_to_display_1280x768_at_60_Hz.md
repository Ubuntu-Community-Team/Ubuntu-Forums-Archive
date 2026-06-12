---
title: "Unable to display 1280x768 at 60 Hz"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by Megapearl on 2007-04-14
Hello,

I'm running ubuntu feisty x64 with 2 screens (one lcd monitor and one dlp projector) lcd is running fine at 1680x1050, but my projector will only display 1280x720.
I'm running in to the problem that i cannot display the native resolution 1280x768 60 Hz at my Optoma HD73 projector. It will display only 1280x720.

I tried different modelines, different options but nothing would help,

Any help would be greatly appreciated.

Regards,
Donald.

My xorg.conf is as following:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "SyncMaster 206bw"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Optoma"
    ModelName      "OPTi OptomaHD73Ev4"
    HorizSync       15.0 - 75.0
    VertRefresh     43.0 - 85.0
    Option         "DPMS"
#   1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
    Modeline "1280x768_60"  80.14  1280 1344 1480 1680  768 769 772 795  +HSync +Vsync
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:7:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:7:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "true"
    Option         "metamodes" "DFP-1: 1680x1050_60 +0+0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "ModeValidation" "NoMaxPClkCheck"
    Option         "UseEdidFreqs" "false"
    Option         "IgnoreEDID" "true"
    Option         "metamodes" "DFP-0: 1280x768_60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1280x768"
    EndSubSection
EndSection

```

Xorg.0.log

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Donald-AMD64 2.6.20-15-generic #2 SMP Fri Apr 13 20:39:41 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 14 13:42:52 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "0"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
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
(II) PCI: 00:00:0: chip 10de,0369 card 1043,8239 rev a1 class 05,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0360 card 1043,8239 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0368 card 1043,8239 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:01:2: chip 10de,036a card 1043,8239 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,036c card 1043,8239 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,036d card 1043,8239 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,036e card f043,8239 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:05:0: chip 10de,037f card 1043,8239 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:05:1: chip 10de,037f card 1043,8239 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:05:2: chip 10de,037f card 1043,8239 rev a2 class 01,01,85 hdr 80
(II) PCI: 00:06:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:06:1: chip 10de,0371 card 1043,81f6 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:08:0: chip 10de,0373 card 1043,8239 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0373 card 1043,8239 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0376 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0b:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,0374 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,0378 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,0375 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 10de,0377 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:0b:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 07:00:0: chip 10de,0193 card 1043,823c rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:6:0), (0,1,1), BCTRL: 0x0a04 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:14:0), (0,6,6), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[4] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[5] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[6] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[7] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 7: bridge is at (0:15:0), (0,7,7), BCTRL: 0x001c (VGA_EN is set)
(II) Bus 7 I/O range:
	[0] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[1] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[2] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[3] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) Bus 7 non-prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) Bus 7 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(7:0:0) nVidia Corporation unknown chipset (0x0193) rev 162, Mem @ 0xfa000000/24, 0xe0000000/28, 0xf8000000/25, I/O @ 0x7c00/7, BIOS @ 0xfbfe0000/17
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
	[0] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[2] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[3] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[4] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[5] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[6] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[8] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[10] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[11] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[12] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[13] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[14] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[36] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[37] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[38] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[39] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[2] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[3] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[4] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[5] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[6] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[8] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[9] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[10] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[11] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[12] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[13] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[14] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[26] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[27] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[28] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[29] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[30] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[36] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[37] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[38] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[39] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
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
	[4] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[6] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[7] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[8] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[9] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[10] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[11] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[12] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[13] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[14] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[15] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[16] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[17] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[18] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[19] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[20] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[21] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[31] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[32] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[33] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[34] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[35] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[37] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[38] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[39] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[40] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[41] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[42] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[43] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[44] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[45] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
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
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:18:52 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 07:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
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
	[4] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[6] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[7] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[8] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[9] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[10] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[11] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[12] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[13] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[14] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[15] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[16] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[17] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[18] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[19] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[20] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[21] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[31] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[32] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[33] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[34] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[35] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[37] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[38] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[39] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[40] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[41] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[42] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[43] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[44] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[45] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[6] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[7] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[8] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[9] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[10] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[11] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[12] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[13] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[14] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[15] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[16] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[17] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[18] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[19] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[20] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[21] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[22] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[23] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[24] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[29] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[31] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[34] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[35] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[36] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[37] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[38] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[39] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[40] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[41] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[42] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[43] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[44] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[45] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[46] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[47] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[48] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
	[49] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[50] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "MetaModes" "DFP-1: 1680x1050_60 +0+0"
(**) NVIDIA(0): Option "TripleBuffer" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTS at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 327680 kBytes
(--) NVIDIA(0): VideoBIOS: 60.80.0d.00.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTS at PCI:7:0:0:
(--) NVIDIA(0):     OPTi OptomaHD73Ev4 (DFP-0)
(--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(0): OPTi OptomaHD73Ev4 (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): OPTi OptomaHD73Ev4 (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP-1:1680x1050_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (99, 98); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "IgnoreEDID" "true"
(**) NVIDIA(1): Option "UseEdidFreqs" "false"
(**) NVIDIA(1): Option "MetaModes" "DFP-0: 1280x768_60 +0+0"
(**) NVIDIA(1): Option "ModeValidation" "NoMaxPClkCheck"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(1):     disabled on all display devices.
(II) NVIDIA(1): NVIDIA GPU GeForce 8800 GTS at PCI:7:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 327680 kBytes
(--) NVIDIA(1): VideoBIOS: 60.80.0d.00.01
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 8800 GTS at PCI:7:0:0:
(--) NVIDIA(1):     OPTi OptomaHD73Ev4 (DFP-0)
(--) NVIDIA(1):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(1): OPTi OptomaHD73Ev4 (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): OPTi OptomaHD73Ev4 (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(1): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(1): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(1): Display Device found referenced in MetaMode: DFP-0
(II) NVIDIA(1): Mode Validation Overrides for OPTi OptomaHD73Ev4 (DFP-0):
(II) NVIDIA(1):     NoMaxPClkCheck
(II) NVIDIA(1): Assigned Display Device: DFP-0
(WW) NVIDIA(1): No valid modes for "DFP-0:1280x768_60+0+0"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 1280 x 720
(WW) NVIDIA(1): OPTi OptomaHD73Ev4 (DFP-0)'s EDID does not contain a maximum
(WW) NVIDIA(1):     image size; cannot compute DPI from OPTi OptomaHD73Ev4
(WW) NVIDIA(1):     (DFP-0)'s EDID.
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdef8000 - 0xfdefbfff (0x4000) MX[B]
	[8] -1	0	0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
	[9] -1	0	0xfe025000 - 0xfe02500f (0x10) MX[B]
	[10] -1	0	0xfe026000 - 0xfe0260ff (0x100) MX[B]
	[11] -1	0	0xfe027000 - 0xfe027fff (0x1000) MX[B]
	[12] -1	0	0xfe028000 - 0xfe02800f (0x10) MX[B]
	[13] -1	0	0xfe029000 - 0xfe0290ff (0x100) MX[B]
	[14] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[15] -1	0	0xfe020000 - 0xfe023fff (0x4000) MX[B]
	[16] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[17] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[18] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[19] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[20] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[21] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[22] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[23] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[24] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[25] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[26] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[27] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[28] 0	0	0x00007c00 - 0x00007c7f (0x80) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[31] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[33] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[35] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[36] -1	0	0x0000c000 - 0x0000c003 (0x4) IX[B]
	[37] -1	0	0x0000c400 - 0x0000c407 (0x8) IX[B]
	[38] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[39] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[40] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[41] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[42] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[43] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[44] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[45] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[46] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[47] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[48] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[49] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[50] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[51] -1	0	0x0000fc00 - 0x0000fc3f (0x40) IX[B]
	[52] -1	0	0x00007c00 - 0x00007c7f (0x80) IX[B](B)
	[53] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[54] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "DFP-1:1680x1050_60+0+0"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "DFP-1:1680x1050_60+0+0"
(--) NVIDIA(0): No video decoder detected
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
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
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded

```

---

### Post by Megapearl on 2007-06-28
Anyone?

---

