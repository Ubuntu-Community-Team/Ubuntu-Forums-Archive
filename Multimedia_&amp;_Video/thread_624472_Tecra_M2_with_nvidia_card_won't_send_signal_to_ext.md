---
title: "Tecra M2 with nvidia card won't send signal to external monitor"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by IndroAppt on 2007-11-27
I see alot of others with similar probs and I have followed the howtos for setting up twinview without success. Ultimately, I really want the tvout to work via svideo but have had no luck. I've attempted to work backwards and get twinview to run an external flat panel first and had no luck with this either.

The log file indicates that the card is detecting the external flat panel monitor ok and is in fact making it monitor 0 while making the internal flat panel monitor 1. The external monitor is receiving no signal though. 

I'm running
Ubuntu Gutsy
Tecra M2
Geforce FX Go5200

Xorg.conf
```
Section "Device"
	Identifier	"nVidia Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo" 		"off"
	Option		"TwinView" 		"on"
	Option		"MetaModes" 		"1024x768,1024x768"
#	Option		"MetaModes" 		"1024x768,640x480; 1024x768,NULL; 800x600,NULL; 640x480,NULL"
#	Option		"UseEDIDFreqs"		"On"
#	Option		"SecondMonitorHorizSync" "30-50"
#	Option		"SecondMonitorVertRefresh" "60"
	Option		"TwinViewOrientation" 	"Clone"
#	Option		"ConnectedMonitor" 	"CRT-0,DFP-0"
#	Option		"ConnectedMonitor" 	"DFP-0,TV"
#	Option		"TVOutFormat" 		"COMPOSITE"
#	Option		"TVStandard" 		"PAL-B"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34M [GeForce FX Go5200 32M/64M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24	
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

xorg.0.log
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "off"
(**) NVIDIA(0): Option "TwinView" "on"
(**) NVIDIA(0): Option "TwinViewOrientation" "Clone"
(**) NVIDIA(0): Option "MetaModes" "1024x768,1024x768"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX Go5200 32M/64M (NV34) at PCI:1:0:0
(II) NVIDIA(0):     (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.63.a3
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX Go5200 32M/64M at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Proview HD-772 (CRT-0)
(--) NVIDIA(0):     TOSHIBA Internal Panel (DFP-0)
(--) NVIDIA(0): Proview HD-772 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): 270.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768,1024x768"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (76, 72); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
```

Overall, I am so impressed with gutsy (been at it for 3 days now) but without tvout support I'm really going to have to revert to micros%*t...

Help, please?

---

### Post by magli on 2007-11-30
Hey,

I just wanted to tell you that I installed gutsy on the exact same laptop as you: tecra m2 w/ nvidia go 5200, last night. I just realized that I am having this problem regarding switching to an external monitor.

I have not looked into it yet, but I will.

Max

---

### Post by IndroAppt on 2007-11-30
Cheers Max, I've tried a few other things with this setup but nothing seems to work. The log files show the card is working fine yet no signal is reaching the monitor (or tv). 

To further taunt me, the tv gives a flicker as X is restarting as if some communication is happening between the computer and monitor but no formal signal.

I look forward to seeing what you think as I'm really new to this and would really appreciate the advice.

Dave

---

### Post by magli on 2007-11-30
One thing I have noted is that if I start the computer with my monitor plugged in, then it works: the monitor is used instead of my laptop display. I can then manage to go from the monitor back to my LCD.. but once my laptop display is in use, I cannot go back to the monitor.

I think that s-video output is a different issue. I have not messed with it in years, and am not sure I have the cables to test it at the moment.

Will report back on any findings as they come.

---

### Post by Gabmg230 on 2008-01-03
I have a tecra M5 with an Nvidia Quadro graphics card. I've been having the same problem with the screen switching but in my case I can't even go from the external to the internal, The function in fact just crashes the computer. I have been trying to setup Twinview and this problem seems to be preventing it to work correctly. I can setup the monitor which is currently active to show half of my desktop but the the monitor which is not being used never turns on to display the other half. I know for sure that my graphics card is capable of this function since it works with xp.

I have searched many forums to find a solution to this problem, but I haven't had very much luck even finding other people with similar problems. I really hope someone can find a way to fix this

---

### Post by IndroAppt on 2008-01-07
Sadly, I didn't have the time and/or patience to work out this problem and I gave up on ubuntu. I will return. 

Good luck

---

### Post by xingmu on 2008-01-13
> **IndroAppt said:**
> Sadly, I didn't have the time and/or patience to work out this problem and I gave up on ubuntu. I will return. 

Good luck

I also have a Tecra M2 with Nvidia and similar problems.  I would like to have a TwinView setup with a LCD connected via VGA and the interal monitor of the laptop.  The problem is that I can only have one or the other, not both.  I've tried all sorts of HOWTOs for around a year, and still no luck.  Is this is a limitation with the drivers or is it a xorg.conf problem??

In case anyone is still reading this thread, here's my xorg.conf file:

```

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
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
    Option         "XkbLayout" "us"
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
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Monitor"
    VendorName     "Unknown"
    ModelName      "TOSHIBA Internal Panel"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "NVIDIA Card"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX Go5200 32M/64M"
    Option         "UseDisplayDevice" "DFP,CRT"
    Option         "MetaModes" "DFP: nvidia-auto-select +1440+0, CRT: nvidia-auto-select +0+0"
    Option         "TwinView" "1"
EndSection

Section "Screen"
    Identifier     "Screen"
    Device         "NVIDIA Card"
    Monitor        "Monitor"
    DefaultDepth    24
EndSection

```

Here's my Xorg.log file:

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux ziggy 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 13 16:35:11 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen" (0)
(**) |   |-->Monitor "Monitor"
(**) |   |-->Device "NVIDIA Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "Xinerama" "0"
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
(II) Loader magic: 0x81ea440
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
(II) PCI: 00:00:0: chip 8086,3340 card 1179,0001 rev 21 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,3341 card 0000,0000 rev 21 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1179,0001 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1179,0001 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1179,0001 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1179,0001 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1179,0001 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1179,0246 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1179,0001 rev 03 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0328 card 1179,0020 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:05:0: chip 8086,1043 card 8086,2581 rev 04 class 02,80,00 hdr 00
(II) PCI: 02:08:0: chip 8086,103d card 1179,0001 rev 83 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 1179,0617 card c000,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0b:1: chip 1179,0617 card c800,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 02:0d:0: chip 1179,0805 card 1179,0001 rev 03 class 08,80,00 hdr 00
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
	[0] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,8), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfce00000 - 0xfcefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x37ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:11:0), (2,3,4), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x33ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (2:11:1), (2,5,8), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[1] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x34000000 - 0x37ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] rev 161, Mem @ 0xfd000000/24, 0xd0000000/28
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xefffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfcefe000 - 0xfcefefff (0x1000) MX[B]
	[1] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[2] -1	0	0x38000a00 - 0x38000aff (0x100) MX[B]
	[3] -1	0	0x38000800 - 0x380009ff (0x200) MX[B]
	[4] -1	0	0x38000400 - 0x380007ff (0x400) MX[B]
	[5] -1	0	0x38000000 - 0x380003ff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[10] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[11] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[12] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[13] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[14] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[21] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfce02000 - 0xfce021ff (0x200) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfcefe000 - 0xfcefefff (0x1000) MX[B]
	[1] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[2] -1	0	0x38000a00 - 0x38000aff (0x100) MX[B]
	[3] -1	0	0x38000800 - 0x380009ff (0x200) MX[B]
	[4] -1	0	0x38000400 - 0x380007ff (0x400) MX[B]
	[5] -1	0	0x38000000 - 0x380003ff (0x400) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[10] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[11] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[12] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[13] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[14] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[15] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[16] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[17] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[21] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfce02000 - 0xfce021ff (0x200) MX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x37ffffff (0x37f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x37ffffff (0x37f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcefe000 - 0xfcefefff (0x1000) MX[B]
	[5] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[6] -1	0	0x38000a00 - 0x38000aff (0x100) MX[B]
	[7] -1	0	0x38000800 - 0x380009ff (0x200) MX[B]
	[8] -1	0	0x38000400 - 0x380007ff (0x400) MX[B]
	[9] -1	0	0x38000000 - 0x380003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xfce02000 - 0xfce021ff (0x200) MX[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[17] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[18] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[19] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[27] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[28] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
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
	[0] -1	0	0x00100000 - 0x37ffffff (0x37f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcefe000 - 0xfcefefff (0x1000) MX[B]
	[5] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[6] -1	0	0x38000a00 - 0x38000aff (0x100) MX[B]
	[7] -1	0	0x38000800 - 0x380009ff (0x200) MX[B]
	[8] -1	0	0x38000400 - 0x380007ff (0x400) MX[B]
	[9] -1	0	0x38000000 - 0x380003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xfce02000 - 0xfce021ff (0x200) MX[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[17] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[18] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[19] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[27] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[28] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x37ffffff (0x37f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfcefe000 - 0xfcefefff (0x1000) MX[B]
	[5] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[6] -1	0	0x38000a00 - 0x38000aff (0x100) MX[B]
	[7] -1	0	0x38000800 - 0x380009ff (0x200) MX[B]
	[8] -1	0	0x38000400 - 0x380007ff (0x400) MX[B]
	[9] -1	0	0x38000000 - 0x380003ff (0x400) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0xfce02000 - 0xfce021ff (0x200) MX[B]
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[20] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[21] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[22] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[23] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[24] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[30] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[31] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "DFP: nvidia-auto-select +1440+0, CRT: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP,CRT"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX Go5200 32M/64M (NV34) at PCI:1:0:0
(II) NVIDIA(0):     (GPU-0)
(--) NVIDIA(0): Memory: 32768 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.63.a3
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX Go5200 32M/64M at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     LG L194WT (CRT-0)
(--) NVIDIA(0):     TOSHIBA Internal Panel (DFP-0)
(--) NVIDIA(0): LG L194WT (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): 270.0 MHz maximum pixel clock
(--) NVIDIA(0): TOSHIBA Internal Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Option "UseDisplayDevice" "CRT, DFP" converted to "CRT-0,
(II) NVIDIA(0):     DFP-0".
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):    
(II) NVIDIA(0):     "DFP:nvidia-auto-select+1440+0,CRT:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 2464 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x37ffffff (0x37f00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfcefe000 - 0xfcefefff (0x1000) MX[B]
	[7] -1	0	0xfceff000 - 0xfcefffff (0x1000) MX[B]
	[8] -1	0	0x38000a00 - 0x38000aff (0x100) MX[B]
	[9] -1	0	0x38000800 - 0x380009ff (0x200) MX[B]
	[10] -1	0	0x38000400 - 0x380007ff (0x400) MX[B]
	[11] -1	0	0x38000000 - 0x380003ff (0x400) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0xfce02000 - 0xfce021ff (0x200) MX[B]
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000cf40 - 0x0000cf7f (0x40) IX[B]
	[22] -1	0	0x00001800 - 0x0000187f (0x80) IX[B]
	[23] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[24] -1	0	0x00001880 - 0x000018bf (0x40) IX[B]
	[25] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[26] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[27] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[28] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[29] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[32] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[33] -1	0	0x0000efe0 - 0x0000efff (0x20) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode
(II) NVIDIA(0):     "DFP:nvidia-auto-select+1440+0,CRT:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(**) Option "HorizEdgeScroll" "0"
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
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event7
(**) Option "Device" "/dev/input/event7"
(--) Synaptics Touchpad touchpad found
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9
```

---

### Post by xingmu on 2008-01-13
I figured it out, finally!!  There was nothing wrong with my Xorg setup after all.  The problem was that the display power settings in my BIOS were set to Auto-Enabled.  When I changed it to Analog+RGB  everything worked!

This fix should have been more obvious to me earlier as I would also only get one screen working when posting and booting up as well.  So in this case, it's clearly not an Xorg problem.  I hope this can help others too!

---

