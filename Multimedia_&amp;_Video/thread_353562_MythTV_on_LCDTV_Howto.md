---
title: "MythTV on LCDTV Howto?"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by alex050478 on 2007-02-04
Here is what i got: 
Asus A8N-VM CSM mobo with integrated geforce 6150
CRT monitor connected via VGA (1280x1024)
Sharp LC-42XD1E 1080P (1920x1080) LCDTV connected on the DVI port with a DVI to HDMI connector. 
Ubuntu Edgy and Mythtv are working on the monitor but i would like to use it in fullHD on the LCDTV. 

I have tried numerous guides but none of them worked for me... This includes twinview and other solutions... 

So here is my last xorg.conf based on the guide at [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Screen 0
        Option  "NoLogo"        "true"
        Option  "RenderAccel"   "true"
        BusID   "PCI:0:5:0"
EndSection

Section "Device"
        Identifier      "Device1"
        Driver "nvidia"
        Screen 1
        BusID   "PCI:0:5:0"
EndSection

Section "Monitor"
        Identifier      "Monitor" #CRT
        HorizSync       30-70
        VertRefresh     50-140
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier "Television" #LCDTV
        HorizSync 30-50
        VertRefresh 60
EndSection


Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor"
        DefaultDepth    24
        Option  	"ConnectedMonitor" "CRT"
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
#        Option  	"TVOutFormat" "COMPOSITE"
        Option  	"TVStandard" "HD1080p"
        Option  	"ConnectedMonitor" "DFP"
        SubSection "Display"
                Depth 24
		Modes "1920x1080_60" "1280x720_60" "720x480_60"
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Basic Layout"
        Screen 0        "Screen0"
        Screen 1        "Screen1" rightof "Screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

The manual of the LCDTV does not say what HorizSync or VertRefresh i should use with the HDMI... But i am not sure if that is the issue here... 

Any ideas would be greatly appreciated!

BTW in the Xorg.0.log, it mentions this: (EE) NVIDIA(1): Unable to find available Display Devices for screen 1.

Here is the  log:

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux mythtv-ubuntu 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  5 03:33:24 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Basic Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Television"
(**) |   |-->Device "Device1"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(II) PCI: 00:00:0: chip 10de,02f0 card 1043,81cd rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1043,81cd rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1043,81cd rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1043,81cd rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1043,81cd rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1043,81cd rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1043,81cd rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1043,81cd rev a2 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,02fc card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 10de,0240 card 1043,81cd rev a2 class 03,00,00 hdr 00
(II) PCI: 00:09:0: chip 10de,0270 card 1043,81bc rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 1043,81bc rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1043,81bc rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1043,81bc rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1043,81bc rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1043,81bc rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,0266 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 10de,cb84 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1043,8141 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 04:08:0: chip 1814,0401 card 182d,9097 rev 00 class 02,80,00 hdr 00
(II) PCI: 04:09:0: chip 3388,0021 card 0000,0000 rev 11 class 06,04,00 hdr 01
(II) PCI: 05:08:0: chip 4444,0016 card 0070,e807 rev 01 class 04,00,00 hdr 00
(II) PCI: 05:09:0: chip 4444,0016 card 0070,e817 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:3:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:4:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:16:0), (0,4,5), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfaa00000 - 0xfaafffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xaff00000 - 0xbfefffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (4:9:0), (4,5,5), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xaff00000 - 0xbfefffff (0x10000000) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51PV [GeForce 6150] rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfebe0000/17
(--) PCI: (5:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xb8000000/26
(--) PCI: (5:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xb4000000/26
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
	[0] -1	0	0xfaaf8000 - 0xfaafffff (0x8000) MX[B]
	[1] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[2] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[3] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[4] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[5] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[6] -1	0	0xb4000000 - 0xb7ffffff (0x4000000) MX[B](B)
	[7] -1	0	0xb8000000 - 0xbbffffff (0x4000000) MX[B](B)
	[8] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[14] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[16] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[20] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfaaf8000 - 0xfaafffff (0x8000) MX[B]
	[1] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[2] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[3] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[4] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[5] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[6] -1	0	0xb4000000 - 0xb7ffffff (0x4000000) MX[B](B)
	[7] -1	0	0xb8000000 - 0xbbffffff (0x4000000) MX[B](B)
	[8] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[14] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[16] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[17] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[20] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
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
	[4] -1	0	0xfaaf8000 - 0xfaafffff (0x8000) MX[B]
	[5] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[6] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xb4000000 - 0xb7ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xb8000000 - 0xbbffffff (0x4000000) MX[B](B)
	[12] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
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
	compiled for 4.0.2, module version = 1.0.8776
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
	compiled for 4.0.2, module version = 1.0.8776
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
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfaaf8000 - 0xfaafffff (0x8000) MX[B]
	[5] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[6] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xb4000000 - 0xb7ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xb8000000 - 0xbbffffff (0x4000000) MX[B](B)
	[12] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[20] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[26] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfaaf8000 - 0xfaafffff (0x8000) MX[B]
	[5] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[6] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xb4000000 - 0xb7ffffff (0x4000000) MX[B](B)
	[11] -1	0	0xb8000000 - 0xbbffffff (0x4000000) MX[B](B)
	[12] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[29] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): ConnectedMonitor string: "CRT"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 at PCI:0:5:0
(--) NVIDIA(0): VideoRAM: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(1): Option "TVStandard" "HD1080p"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): TV Standard string: "HD1080p"
(II) NVIDIA(1): NVIDIA GPU GeForce 6150 at PCI:0:5:0
(--) NVIDIA(1): VideoRAM: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 05.51.22.26.07
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(1):     CRT-0
(--) NVIDIA(1): CRT-0: 350.0 MHz maximum pixel clock
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfaaf8000 - 0xfaafffff (0x8000) MX[B]
	[8] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[9] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[10] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[11] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[12] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[13] -1	0	0xb4000000 - 0xb7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xb8000000 - 0xbbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[16] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[29] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
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
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
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
error opening security policy file /usr/lib/xserver/SecurityPolicy
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
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```

---

### Post by scottie_z on 2007-02-06
Alex,

Have you first verified that your HDTV works correctly in a solo configuration?  If you find that it does not, your TV may need a custom modeline.  The appended thread describes how to create one (ignore the Intel-specific stuff, as well as the "MonitorLayout" option -- those apply to intel chips in laptops with an external LCD).  Otherwise, I don't know anything about twinview -- I'd like to learn though, so please post back with your xorg.conf if you get it working!

[http://www.ubuntuforums.org/showthread.php?t=203905]("http://www.ubuntuforums.org/showthread.php?t=203905")
(post #10, steps 1 and 2 will get you a modeline)

---

### Post by alex050478 on 2007-02-08
Thanks for the reply! 

What is strange is that when i boot ubuntu with only the LCDTV attached, i do not get anything on the screen, no text and also no gnome... When i boot winXP i don't see grub either, nor the windows loading screen, but then i do get the desktop. Also i just tested in windows and it does support many resolutions between 640x480 up to 1920x1080... :confused: 

So before i start looking for custome modlines, maybe i should be trying to get it to work in text based linux, don't you think?   I think the lcdtv or the dvi connector is not being detected or something... :confused: Any ideas how to find this out? 

```
lspci

00:05.0 VGA compatible controller: nVidia Corporation C51PV [GeForce 6150] (rev a2)
```

---

### Post by BeachBum on 2007-02-09
EDIT: I just re-read your posts and now realize you are not trying to use two monitors at once, and that you could use the LCD TV in Windows.  In that case, I don't have experience with using the DVI adapter, however another good resource for the graphics chipset+linux is here:
[http://forums.anandtech.com/textthread.aspx?catid=29&threadid=1762814&arctab=y](http://forums.anandtech.com/textthread.aspx?catid=29&threadid=1762814&arctab=y)


I have a motherboard with the same onboard graphics chipset (Nvidia 6150), and from other forums, this particular configuration is not supported:

> 
**Supported Configurations by Onboard Video **

The following combinations are supported in DualView mode: 

digital monitor (onboard DVI) + analog monitor (onboard VGA) 

digital monitor (onboard DVI) + TV (onboard TV out)

**Unsupported Configurations by Onboard Video **

As GeForce 6150 has only one RAMDAC (Random Access Memory Digital/Analog Converter) and hence two analog outs are impossible, the following combinations are not supported: 

analog monitor (onboard DVI) + analog monitor (onboard VGA). (First of all connecting an analog monitor to onboard DVI is physically impossible because the onboard DVI connector is DVI-D that lacks 4-pin holes and hence a DVI to VGA adapter cannot be used.) 

analog monitor (onboard VGA) + TV (onboard TV out). (Note that signals from onboard TV out are analog.)


[http://forums.anandtech.com/messageview.cfm?catid=29&threadid=1803985](http://forums.anandtech.com/messageview.cfm?catid=29&threadid=1803985)

I wanted to do the same thing, run an old LDC monitor off VGA and an LDC TV using the DVI interface.  I found that the limitation was my LCD TV; the DVI input was not designed to handle a computer interface (resolutions and overlay and stuff like that), and was instead designed to handle other A/V peripherals (like DVD players).  So the only option for quality viewing using two monitors was to use a DVI to VGA converter, but as mentioned above, that is not supported.   

I looked up the manual of your TV here:
[http://www.tradenet.sharp.co.uk/files/Consumer_Electronics/LCD_Television/LC42XD1E/LC42XD1E145.pdf](http://www.tradenet.sharp.co.uk/files/Consumer_Electronics/LCD_Television/LC42XD1E/LC42XD1E145.pdf)
and found that the only PC supported input is RGB (as noted in the Connecting a PC section).  They say you can use a DVI to RGB cable, but I *think* that RGB is analog, which means you would have two analog connections to your motherboard, which is not supported.   

Based on your post, you hooked up your LCD TV from DVI to HDMI, which should be supported on the PC side (ok with your hardware if your CTR is not hooked up), but may look lousy or not be visible at all on the TV side (because your TV has a specific PC hookup, most likely meaning other ports will either look lousy in comparison or not be viewable).   

Take a look at those sites I mentioned, and let us know how it goes.  Oh, and nice TV :)

Also forgot to mention; some Windows users who had TV's hooked up using the DVI interface didn't see the loading screen either, and that this had something to do with the digital interface initializing later in the boot process, or something like that.

---

### Post by alex050478 on 2007-02-10
Thanks again! I will look up the sites you mentioned! 

I have made some progress at using my lcdtv in 1080p as a single setup when i remove some lines from the xorg.conf. 

Here is my current xorg.conf.   I will post a new one when i have managed to get both the crt and the lcd working at the same time. 

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

# Section "Device"
#        Identifier      "Device0"
#        Driver          "nvidia"
#        Screen 0
#        Option  "NoLogo"        "true"
#        Option  "RenderAccel"   "true"
#        BusID   "PCI:0:5:0"
# EndSection

Section "Device"
        Identifier      "Device1"
        Driver "nvidia"
#        Screen 1
        BusID   "PCI:0:5:0"
EndSection

# Section "Monitor"
#        Identifier      "Monitor" #CRT
#        HorizSync       30-70
#        VertRefresh     50-140
#        Option          "DPMS"
# EndSection

Section "Monitor"
        Identifier "LCDTV"
        Option "DPMS"
EndSection


# Section "Screen"
#        Identifier      "Screen0"
#        Device          "Device0"
#        Monitor         "Monitor"
#        DefaultDepth    24
#        Option  	"ConnectedMonitor" "CRT"
#	SubSection "Display"
#		Depth 24
#		Modes "1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
# EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "LCDTV"
        DefaultDepth    24
#        Option  	"TVOutFormat" "COMPOSITE"
        Option  	"TVStandard" "HD1080p"
        Option  	"ConnectedMonitor" "DFP"
#        SubSection "Display"
#                Depth 24
#		Modes "1920x1080_60" "1280x720_60" "720x480_60"
#        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Basic Layout"
#        Screen 0        "Screen0"
#        Screen 1        "Screen1" rightof "Screen0"
	Screen 1	"Screen1"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Eventually i will only need the lcdtv setup but now a crt is handy for configuration of myth, etc. Typing like this and watching big tv is giving me a stiff neck! :roll:

---

### Post by alex050478 on 2007-02-10
Ok i got it working! Somehow when i have the Option "ConnectedMonitor" "CRT" enabled under  the "screen" section (the one describing the CRT monitor), then my LCDTV goes black! Don't ask me why but it does! 

Anyways, here is the final version of my xorg.conf. Thanks for all the help!

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Screen 0
        Option  "NoLogo"        "true"
        Option  "RenderAccel"   "true"
        BusID   "PCI:0:5:0"
EndSection

Section "Device"
        Identifier      "Device1"
        Driver "nvidia"
        Screen 1
        BusID   "PCI:0:5:0"
EndSection

Section "Monitor"
        Identifier      "Monitor" #CRT
#        HorizSync       30-70
#        VertRefresh     50-140
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier "LCDTV"
        Option "DPMS"
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor"
        DefaultDepth    24
#        Option  	"ConnectedMonitor" "CRT" # this makes lcdtv go black
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "LCDTV"
        DefaultDepth    24
#        Option  	"TVOutFormat" "COMPOSITE"
        Option  	"TVStandard" "HD1080p"
        Option  	"ConnectedMonitor" "DFP"
#        SubSection "Display"
#                Depth 24
#		Modes "1920x1080_60" "1280x720_60" "720x480_60"
#        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Basic Layout"
        Screen 0        "Screen0"
        Screen 1        "Screen1" rightof "Screen0"
	Screen 1	"Screen1"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

