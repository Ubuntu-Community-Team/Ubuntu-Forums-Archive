---
title: "help with manual modeline based on EDID info"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by alex050478 on 2007-08-02
EDIT: FOR A WORKAROUND TO THIS ISSUE, SEE 4TH POST!

I need some help with a custum modeline in xorg.conf.

My hardware:
mobo: Asus a8n-vm csm with integrated Nvidia Geforce 6150
Screen: Sharp LC-42XD1E with DVI --> HDMI

I have a working configuration when i use a 2m cable. When i disconnect the 2m cable and put a 10m cable between my grafics card and the screen, it still works with good quality. The problem is when i startx with the long cable attached. According to the log, this long cable prevents xorg from reading EDID data because there is to much resistance on the cable or the chip on the grafics card in not sensitive enough... Now if i understand this correctly, the workaround is a custom modeline in xorg and  Option "UseEDID" "FALSE" in the device section.

So the last 6 days i have been  trying many  online modeline generators but  none of them seem to work for me... . Half of them i cannot use because ineed tio fill in values i cannot find anywhere! 

Also had a look at videogen but it needs the videocard dot clock which i cannot find...

So i am pretty desperate now and hope you can help.

Here is my xorg.conf:
```

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "dbe"
	Load  "GLcore"
	Load  "xtrap"
	Load  "record"
	Load  "extmod"
	Load  "glx"
	Load  "type1"
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
	Option		"Protocol"		"auto" 	#"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
#        Screen 0
#        Option  "NoLogo"        "true"
	Option	"UseEDID" 	"FALSE"
        Option  "RenderAccel"   "true"
        BusID   "PCI:0:5:0"
	Option "XvmcUsesTextures" "true"
	Option "AllowGLXWithComposite" "true"
	Option "AddARGBGLXVisuals" "true"
EndSection

Section "Monitor"
        Identifier "LCDTV"
#	DisplaySize  487 274
	Option "useEdidDpi" 	"FALSE"
	Option "DPI"	"100 x 100"
	HorizSync	15-75 # kHz
	VertRefresh	49-61 # Hz
	#Modeline "1920x1080_50" 148.50   1920 1929 2160 2472
					 1080 1080 1082 1113 
#	Modeline "1920x1080_50" 148.50   1920 1952 2496 2528
#					 1080 1103 1112 1135 +vsync +hsync
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "LCDTV"
        DefaultDepth    24
#	Option "UseEdidFreqs" "FALSE"
#        Option         "TVOutFormat" "COMPOSITE"
        Option          "TVStandard" "HD1080p"
        Option          "ConnectedMonitor" "DFP"
	Option 		"ModeValidation" "AllowNon60HzDFPModes"
#	Option     	"UseEvents" "True"    #use with 9xxx series drivers
        SubSection "Display"
               	Depth 24
               	Modes "1920x1080_50" "1280x720_60" "720x480_60"
		Virtual 1920 1080
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Basic Layout"
        Screen 0        "Screen0"
#        Screen 1        "Screen1" rightof "Screen0"
#        Screen 1        "Screen1"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#        Option  "BlankTime"  "1"  # Blank the screen (Fake)
  	Option  "StandbyTime"  "5"  # Turn off screen (DPMS)
#  	Option  "SuspendTime"  "2"  # Full suspend
  	Option  "OffTime"  "10"  # Turn off
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
	Option "RENDER" "true"
EndSection

```

When i use this config it says in the log that there are no valid modes for my resolutions and then defaults to 640x480 which my screen does not support.

Here is the EDID data from Xorg.0.log when using short cable and  startx -logverbose 5 and without Option "UseEDID"  "FALSE" in xorg.conf

```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux moon91 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 31 16:53:24 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Basic Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "LCDTV"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
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
(**) RgbPath set to "/etc/X11/rgb"
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "StandbyTime" "5"
(**) Option "OffTime" "10"
(**) Extension "RENDER" is enabled
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(II) No APM support in BIOS or kernel
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
(--) using VT number 3

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
(II) PCI: 00:0f:0: chip 10de,0267 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 10de,cb84 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1043,8141 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
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
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51PV [GeForce 6150] rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfebe0000/17
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
	[0] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[3] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[4] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[5] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[6] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[17] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[19] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[23] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[3] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[4] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[5] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[6] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[17] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[19] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[23] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
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
	[4] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[29] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "xtrap"
(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DEC-XTRAP
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
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
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
(--) Chipset NVIDIA GPU found
(II) NVIDIA(0): Found 1 NVIDIA X Screens
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
	[4] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[29] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[32] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Option "TVStandard" "HD1080p"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Option "XvMCUsesTextures" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "UseEdidDpi" "TRUE"
(**) NVIDIA(0): Option "DPI" "100 x 100"
(**) NVIDIA(0): Option "UseEvents" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "true"
(**) NVIDIA(0): Option "ModeValidation" "AllowNon60HzDFPModes"
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(**) NVIDIA(0): TV Standard string: "HD1080p"
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(II) NVIDIA(0): GPU Architecture: 0x40
(II) NVIDIA(0): GPU Implementation: 0x4e
(II) NVIDIA(0): GPU Revision: 0xa2
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.07
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, DFP-0, TV-0
(II) NVIDIA(0): Bus detected as Integrated
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): VPES : 1
(II) NVIDIA(0): SPS  : 2
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing constraints for  : GeForce 6150
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 8192
(II) NVIDIA(0):     Horizontal Blank Start   : 8192
(II) NVIDIA(0):     Horizontal Blank Width   : 4096
(II) NVIDIA(0):     Horizontal Sync Start    : 8184
(II) NVIDIA(0):     Horizontal Sync Width    : 504
(II) NVIDIA(0):     Horizontal Total Width   : 8224
(II) NVIDIA(0):     Vertical Visible Height  : 8192
(II) NVIDIA(0):     Vertical Blank Start     : 8192
(II) NVIDIA(0):     Vertical Blank Width     : 256
(II) NVIDIA(0):     Veritcal Sync Start      : 8191
(II) NVIDIA(0):     Vertical Sync Width      : 15
(II) NVIDIA(0):     Vertical Total Height    : 8193
(II) NVIDIA(0): 
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 40
(II) NVIDIA(0):     Vertical Total Height    : 2
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(0): 
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     SHARP HDMI (DFP-0)
(--) NVIDIA(0): SHARP HDMI (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): SHARP HDMI (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(0): SHARP HDMI (DFP-0): Native FlatPanel Scaling is supported
(--) NVIDIA(0): SHARP HDMI (DFP-0): DFP modes are not limited to 60 Hz refresh
(--) NVIDIA(0):     rate
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for SHARP HDMI (DFP-0) ---
(--) NVIDIA(0): EDID Version                 : 1.3
(--) NVIDIA(0): Manufacturer                 : SHP
(--) NVIDIA(0): Monitor Name                 : SHARP HDMI
(--) NVIDIA(0): Product ID                   : 4072
(--) NVIDIA(0): 32-bit Serial Number         : 16843009
(--) NVIDIA(0): Serial Number String         : 
(--) NVIDIA(0): Manufacture Date             : 2006, week 0
(--) NVIDIA(0): DPMS Capabilities            : Active Off
(--) NVIDIA(0): Prefer first detailed timing : Yes
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 1150mm x 650mm
(--) NVIDIA(0): Valid HSync Range            : 15 kHz - 75 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 49 Hz - 61 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 170.0 MHz
(--) NVIDIA(0): 
(--) NVIDIA(0): Detailed Timings:
(--) NVIDIA(0):   1920 x 1080 @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 148.50 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2448
(--) NVIDIA(0):     HSyncEnd, HTotal : 2492, 2640
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   1920 x 1080 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 148.50 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
(--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   1280 x 720  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1720
(--) NVIDIA(0):     HSyncEnd, HTotal : 1760, 1980
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   1280 x 720  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1390
(--) NVIDIA(0):     HSyncEnd, HTotal : 1430, 1650
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 732
(--) NVIDIA(0):     HSyncEnd, HTotal : 796, 864
(--) NVIDIA(0):     VRes, VSyncStart : 576, 581
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 625
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0): 
(--) NVIDIA(0): CEA-861B Timings:
(--) NVIDIA(0):   1920 x 1080 @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 148.50 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2448
(--) NVIDIA(0):     HSyncEnd, HTotal : 2492, 2640
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 31
(--) NVIDIA(0):   1920 x 1080 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 148.35 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
(--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 16
(--) NVIDIA(0):   1920 x 1080 @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2448
(--) NVIDIA(0):     HSyncEnd, HTotal : 2492, 2640
(--) NVIDIA(0):     VRes, VSyncStart : 540, 542
(--) NVIDIA(0):     VSyncEnd, VTotal : 547, 562
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 20
(--) NVIDIA(0):   1920 x 1080 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.18 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
(--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
(--) NVIDIA(0):     VRes, VSyncStart : 540, 542
(--) NVIDIA(0):     VSyncEnd, VTotal : 547, 562
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 5
(--) NVIDIA(0):   1280 x 720  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1720
(--) NVIDIA(0):     HSyncEnd, HTotal : 1760, 1980
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 19
(--) NVIDIA(0):   1280 x 720  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.18 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1390
(--) NVIDIA(0):     HSyncEnd, HTotal : 1430, 1650
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 4
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 732
(--) NVIDIA(0):     HSyncEnd, HTotal : 796, 864
(--) NVIDIA(0):     VRes, VSyncStart : 576, 581
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 625
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 18
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 736
(--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
(--) NVIDIA(0):     VRes, VSyncStart : 480, 489
(--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 3
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 732
(--) NVIDIA(0):     HSyncEnd, HTotal : 796, 864
(--) NVIDIA(0):     VRes, VSyncStart : 576, 581
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 625
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 17
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 736
(--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
(--) NVIDIA(0):     VRes, VSyncStart : 480, 489
(--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 2
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1464
(--) NVIDIA(0):     HSyncEnd, HTotal : 1590, 1728
(--) NVIDIA(0):     VRes, VSyncStart : 288, 290
(--) NVIDIA(0):     VSyncEnd, VTotal : 293, 312
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 22
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1478
(--) NVIDIA(0):     HSyncEnd, HTotal : 1602, 1716
(--) NVIDIA(0):     VRes, VSyncStart : 240, 244
(--) NVIDIA(0):     VSyncEnd, VTotal : 247, 262
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 7
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1464
(--) NVIDIA(0):     HSyncEnd, HTotal : 1590, 1728
(--) NVIDIA(0):     VRes, VSyncStart : 288, 290
(--) NVIDIA(0):     VSyncEnd, VTotal : 293, 312
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 21
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1478
(--) NVIDIA(0):     HSyncEnd, HTotal : 1602, 1716
(--) NVIDIA(0):     VRes, VSyncStart : 240, 244
(--) NVIDIA(0):     VSyncEnd, VTotal : 247, 262
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 6
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 25.17 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 640, 656
(--) NVIDIA(0):     HSyncEnd, HTotal : 752, 800
(--) NVIDIA(0):     VRes, VSyncStart : 480, 490
(--) NVIDIA(0):     VSyncEnd, VTotal : 492, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 1
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for SHARP HDMI (DFP-0) ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Mode Validation Overrides for SHARP HDMI (DFP-0):
(II) NVIDIA(0):     AllowNon60HzDFPModes
(II) NVIDIA(0): Frequency information for SHARP HDMI (DFP-0):
(II) NVIDIA(0):   HorizSync   : 28.000-33.000 kHz
(II) NVIDIA(0):   VertRefresh : 43.000-72.000 Hz
(II) NVIDIA(0):     (HorizSync from Conservative Defaults)
(II) NVIDIA(0):     (VertRefresh from Conservative Defaults)
(II) NVIDIA(0): 
(II) NVIDIA(0): Native backend timings for SHARP HDMI (DFP-0):
(II) NVIDIA(0):   720 x 576 @ 50 Hz
(II) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):     HRes, HSyncStart :  720,  732
(II) NVIDIA(0):     HSyncEnd, HTotal :  796,  864
(II) NVIDIA(0):     VRes, VSyncStart :  576,  581
(II) NVIDIA(0):     VSyncEnd, VTotal :  586,  625
(II) NVIDIA(0):     H/V Polarity     : -/-
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for SHARP HDMI (DFP-0) ---
(II) NVIDIA(0): "nvidia-auto-select" :  720 x  576 @  50.0 Hz  (from: EDID)
(II) NVIDIA(0): "720x576"            :  720 x  576 @  50.0 Hz  (from: EDID)
(II) NVIDIA(0): "720x576_50"         :  720 x  576 @  50.0 Hz  (from: EDID)
(II) NVIDIA(0): "720x480"            :  720 x  480 @  59.9 Hz  (from: EDID)
(II) NVIDIA(0): "720x480_60"         :  720 x  480 @  59.9 Hz  (from: EDID)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  60.0 Hz  (from: VESA)
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  60.0 Hz  (from: VESA)
(II) NVIDIA(0): "640x480_60_0"       :  640 x  480 @  59.9 Hz  (from: EDID)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): --- End of ModePool for SHARP HDMI (DFP-0): ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "1920x1080_50"
(II) NVIDIA(0):     "1280x720_60"
(II) NVIDIA(0):     "720x480_60"
(WW) NVIDIA(0): No valid modes for "1920x1080_50"; removing.
(WW) NVIDIA(0): No valid modes for "1280x720_60"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "720x480_60":
(II) NVIDIA(0):     Bounding Box: [0, 0, 720, 480]
(II) NVIDIA(0):     SHARP HDMI (DFP-0): "720x480_60"
(II) NVIDIA(0):         Size          : 720 x 480
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 720 x 480
(II) NVIDIA(0):         Position      : [0, 0, 720, 480]
(II) NVIDIA(0): Virtual screen size determined to be 720 x 480
(II) NVIDIA(0): 
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0): 
(II) NVIDIA(0): "640x480"      :  640 x  480 @  60.0 Hz 
(II) NVIDIA(0): "640x480_60_0" :  640 x  480 @  59.9 Hz 
(II) NVIDIA(0): "320x240"      :  320 x  240 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): 
(**) NVIDIA(0): DPI set to (100, 100); computed from "DPI" X config option
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
	[7] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[8] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[9] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[10] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[11] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[12] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[13] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[26] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[29] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[31] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[35] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): Memory mapped
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "720x480_60"
(II) NVIDIA(0): DFP-0 assigned CRTC 0
(II) NVIDIA(0): First mode initialized
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(II) Loading extension NV-CONTROL
(II) NVIDIA(0): Screen initialization complete
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
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "auto"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5 6 7"
(**) Configured Mouse: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Configured Mouse: Buttons: 11
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/mice"
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
GetModeLine - scrn: 0 clock: 27000
GetModeLine - hdsp: 720 hbeg: 736 hend: 800 httl: 856
              vdsp: 480 vbeg: 489 vend: 495 vttl: 525 flags: 10


```

So how can i use this info in a custom modeline? I have looked up the meaning of the modeline values on wikipedia [HTML]http://en.wikipedia.org/wiki/Modeline[/HTML] but am at a loss when trying to find the front porch, sync pulse, and back porch values...

Any help is greatly appreciated!

---

### Post by david_2001 on 2007-08-02
There's an easier way than deriving the settings from the logs - I wouldn't even want to work out how to do that task successfully!  With the short monitor cable connected, set the monitor to the mode you need and then run
```
xvidtune -show
```
in a terminal (xvidtune should be part of the default Ubuntu install, if not then it's in the repositories).  This will print the modeline settings in a format ready for inclusion in your xorg.conf.

---

### Post by alex050478 on 2007-08-02
Thanks David! This should make things a lot easyer!  

So i did startx with short cable connected and did the xvidtune -show command and it generated this modeline:
```

"1920x1080"   148.50   1920 1928 2160 2472   1080 1080 1082 1113 +hsync +vsync

```

Now when i insert his one into my xorg.conf and enable Option	"UseEDID"  "FALSE" , then i get this log saying No valid modes for "1080p50"; removing::
```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux moon91 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  3 00:03:23 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Basic Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "LCDTV"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
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
(**) RgbPath set to "/etc/X11/rgb"
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "StandbyTime" "5"
(**) Option "OffTime" "10"
(**) Extension "RENDER" is enabled
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(II) No APM support in BIOS or kernel
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
(--) using VT number 3

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
(II) PCI: 00:0f:0: chip 10de,0267 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 10de,cb84 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1043,8141 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
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
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51PV [GeForce 6150] rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfebe0000/17
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
	[0] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[3] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[4] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[5] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[6] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[17] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[19] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[23] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[3] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[4] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[5] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[6] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[17] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[19] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[23] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
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
	[4] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[29] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "xtrap"
(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DEC-XTRAP
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
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
	[4] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[29] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[32] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "UseEDID" "FALSE"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Option "TVStandard" "HD1080p"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "XvMCUsesTextures" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "UseEdidDpi" "FALSE"
(**) NVIDIA(0): Option "DPI" "100 x 100"
(**) NVIDIA(0): Option "UseEvents" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TV Standard string: "HD1080p"
(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 310.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1080p50"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(**) NVIDIA(0): Virtual screen size configured to be 1920 x 1080
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
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
	[7] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[8] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[9] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[10] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[11] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[12] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[13] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[26] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[29] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[31] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[35] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Unable to connect to the ACPI daemon; the ACPI daemon may not
(II) NVIDIA(0):     be running or the "AcpidSocketPath" X configuration option
(II) NVIDIA(0):     may not be set correctly.  When the ACPI daemon is
(II) NVIDIA(0):     available, the NVIDIA X driver can use it to receive ACPI
(II) NVIDIA(0):     events.  For details, please see the "ConnectToAcpid" and
(II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) NVIDIA(0):     Config Options in the README.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
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
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "auto"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5 6 7"
(**) Configured Mouse: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Configured Mouse: Buttons: 11
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

```

Now same setup but with the EDID enabled:
```


X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux moon91 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  3 00:09:33 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Basic Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "LCDTV"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
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
(**) RgbPath set to "/etc/X11/rgb"
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "StandbyTime" "5"
(**) Option "OffTime" "10"
(**) Extension "RENDER" is enabled
(WW) Open ACPI failed (/var/run/acpid.socket) (Connection refused)
(II) No APM support in BIOS or kernel
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
(--) using VT number 3

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
(II) PCI: 00:0f:0: chip 10de,0267 card 1043,81bc rev a1 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 10de,cb84 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:14:0: chip 10de,0269 card 1043,8141 rev a1 class 06,80,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
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
(II) Bus 4: bridge is at (0:16:0), (0,4,4), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(0:5:0) nVidia Corporation C51PV [GeForce 6150] rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfebe0000/17
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
	[0] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[3] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[4] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[5] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[6] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[17] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[19] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[23] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[1] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[2] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[3] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[4] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[5] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[6] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[7] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[12] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[14] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[16] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[17] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[19] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[23] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
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
	[4] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[29] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "xtrap"
(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DEC-XTRAP
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:05:0
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
	[4] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[18] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[20] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[23] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[25] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[29] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[5] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[6] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[7] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[8] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[9] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[10] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[11] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[26] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[28] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[32] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP"
(**) NVIDIA(0): Option "TVStandard" "HD1080p"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "XvMCUsesTextures" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "UseEdidDpi" "FALSE"
(**) NVIDIA(0): Option "DPI" "100 x 100"
(**) NVIDIA(0): Option "UseEvents" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TV Standard string: "HD1080p"
(**) NVIDIA(0): ConnectedMonitor string: "DFP"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     SHARP HDMI (DFP-0)
(--) NVIDIA(0): SHARP HDMI (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): SHARP HDMI (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1080p50"
(**) NVIDIA(0): Virtual screen size configured to be 1920 x 1080
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
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
	[7] -1	0	0xfebd7000 - 0xfebd7fff (0x1000) MX[B]
	[8] -1	0	0xfebd8000 - 0xfebdbfff (0x4000) MX[B]
	[9] -1	0	0xfebdc000 - 0xfebdcfff (0x1000) MX[B]
	[10] -1	0	0xfebdd000 - 0xfebddfff (0x1000) MX[B]
	[11] -1	0	0xfebdfc00 - 0xfebdfcff (0x100) MX[B]
	[12] -1	0	0xfebde000 - 0xfebdefff (0x1000) MX[B]
	[13] -1	0	0xfebe0000 - 0xfebfffff (0x20000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d080 - 0x0000d087 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[26] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[29] -1	0	0x0000e080 - 0x0000e083 (0x4) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[31] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[35] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Unable to connect to the ACPI daemon; the ACPI daemon may not
(II) NVIDIA(0):     be running or the "AcpidSocketPath" X configuration option
(II) NVIDIA(0):     may not be set correctly.  When the ACPI daemon is
(II) NVIDIA(0):     available, the NVIDIA X driver can use it to receive ACPI
(II) NVIDIA(0):     events.  For details, please see the "ConnectToAcpid" and
(II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
(II) NVIDIA(0):     Config Options in the README.
(II) NVIDIA(0): Setting mode "1080p50"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
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
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "auto"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "auto"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5 6 7"
(**) Configured Mouse: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Configured Mouse: Buttons: 11
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

``` 

So the mode gets validated but only when using EDID data?!?!?! Any ideas?

Thanks again for any help you can provide!

---

### Post by alex050478 on 2007-08-03
Ok, i have found a workaround on Nvidia forums. 

When having the screen working, i used nvidia-settings and used the Aquire EDID feature to export the EDID data to a file. After that you ahve to refer to it in your xorg.conf. 

I hope this helps anyone with the same issue.

```

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "dbe"
	Load  "GLcore"
	Load  "xtrap"
	Load  "record"
	Load  "extmod"
	Load  "glx"
	Load  "type1"
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
	Option		"Protocol"		"auto" 	#"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
#        Screen 0
        Option  "NoLogo"        "true"
	Option	"CustomEDID"	"DFP-0:/etc/X11/edid.bin"
#	Option	"UseEDID" 	"FALSE"
#	Option	"UseEDIDFreqs"	"false"
        Option  "RenderAccel"   "true"
        BusID   "PCI:0:5:0"
	Option "XvmcUsesTextures" "true"
	Option "AllowGLXWithComposite" "true"
	Option "AddARGBGLXVisuals" "true"
EndSection

Section "Monitor"
        Identifier "LCDTV"
#	DisplaySize  487 274
	Option "useEdidDpi" 	"FALSE"
	Option "DPI"	"100 x 100"
	HorizSync	15-75 # kHz
	VertRefresh	49-61 # Hz
	Modeline "1080p50"   148.50   1920 1928 2160 2472   1080 1080 1082 1113 +hsync +vsync
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "LCDTV"
        DefaultDepth    24
#	Option "UseEdidFreqs" "FALSE"
#        Option         "TVOutFormat" "COMPOSITE"
        Option          "TVStandard" "HD1080p"
        Option          "ConnectedMonitor" "DFP"
#	Option 		"ModeValidation" "AllowNon60HzDFPModes"
	Option     	"UseEvents" "True"    #use with 9xxx series drivers
        SubSection "Display"
               	Depth 24
               	Modes "1080p50"  
		Virtual 1920 1080
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "Basic Layout"
        Screen 0        "Screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#        Option  "BlankTime"  "1"  # Blank the screen (Fake)
  	Option  "StandbyTime"  "5"  # Turn off screen (DPMS)
#  	Option  "SuspendTime"  "2"  # Full suspend
  	Option  "OffTime"  "10"  # Turn off
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
	Option "RENDER" "true"
EndSection


```

---

