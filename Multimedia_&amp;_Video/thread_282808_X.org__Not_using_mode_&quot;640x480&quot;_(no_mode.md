---
title: "X.org:  Not using mode &quot;640x480&quot; (no mode of this name) !!!!"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by .t. on 2006-10-23
I am trying to get X.org (on a Dell Inspiron 6000; with Intel i915) to allow me to use 640x480 (amongst other resolutions). Don't ask why. Anyway, it obviously hates me. It never used to, it used to work just fine. Thing is, I can't remember what I did. Now, I cannot use the mode, and Xorg.0.log just gives "Not using mode "640x480" (no mode of this name)". 915resolution knows it's there.

Here's my xorg.conf:```
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
	Option		"XkbLayout"	"gb"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
   Option "LeftEdge" "130"
   Option "RightEdge" "840"
   Option "TopEdge" "130"
   Option "BottomEdge" "640"
   Option "FingerLow" "7"
   Option "FingerHigh" "8"
   Option "MaxTapTime" "180"
   Option "MaxTapMove" "110"
   Option "EmulateMidButtonTime" "75"
   Option "VertScrollDelta" "20"
   Option "HorizScrollDelta" "20"
   Option "MinSpeed" "0.60"
   Option "MaxSpeed" "1.10"
   Option "AccelFactor" "0.030"
   Option "EdgeMotionMinSpeed" "200"
   Option "EdgeMotionMaxSpeed" "200"
   Option "UpDownScrolling" "1"
   Option "CircularScrolling" "1"
   Option "CircScrollDelta" "0.1"
   Option "CircScrollTrigger" "2"
   Option "SHMConfig" "on"
   Option "Emulate3Buttons" "on"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"DisplayInfo" "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	DisplaySize	332 212
	HorizSync	45.71-50.53
	VertRefresh	60
	Option		"DPMS"	"true"
	Option		"DDC"	"false"
	# 640x480 @ 60.00 Hz (GTF) hsync: 29.82 kHz; pclk: 23.86 MHz
	Modeline "640x480_60.00"  23.86  640 656 720 800  480 481 484 497  -HSync +Vsync
	# 800x600 @ 60.00 Hz (GTF) hsync: 37.32 kHz; pclk: 38.22 MHz
	Modeline "800x600_60.00"  38.22  800 832 912 1024  600 601 604 622  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	Option "XaaNoOffscreenPixmaps"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
		Virtual		1280 800
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
		Virtual		1280 800
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
		Virtual		1280 800
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
		Virtual		1280 800
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
		Virtual		1280 800
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
		Virtual		1280 800
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
  Option  "BlankTime"  "5"  # Blank the screen after 5 minutes (Fake)
  Option  "StandbyTime"  "10"  # Turn off screen after 10 minutes (DPMS)
  Option  "SuspendTime"  "20"  # Full suspend after 20 minutes
  Option  "OffTime"  "30"  # Turn off after half an hour
  Option  "AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "true"
EndSection
```Output of 915resolution -l:```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 60 : 400x772, 8 bits/pixel
Mode 61 : 400x772, 16 bits/pixel
Mode 62 : 400x772, 32 bits/pixel
Mode 63 : 512x771, 8 bits/pixel
Mode 64 : 512x771, 16 bits/pixel
Mode 65 : 512x771, 32 bits/pixel
Mode 66 : 1280x800, 8 bits/pixel
Mode 67 : 1280x800, 16 bits/pixel
Mode 68 : 1280x800, 32 bits/pixel
```And I'll attach Xorg.0.log. I had to add .gpl to the filename. But I don't really care about its licence...

---

### Post by taurus on 2006-10-23
Why don't you config your X again but pick whichever resolution you want to use!

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by CatKiller on 2006-10-23
Doesn't 915resolution map the lower resolutions to higher resolutions to get round the limited number of video modes that that chipset can cope with? That's what I thought it did, but I've never used it.

---

