---
title: "cant get 1440x900 to work, Intel 82845G/GL, V7 R19W12 monitor, ubuntu 6.10"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by hectorkatz on 2007-11-12
sorry to bother you all but I am unable to get 1440x900 to work with my card...I have read a great number of previous posts, but nothing seems to work.  I have already tried to install and load the intel driver but all I get is a blank screen.  I have tried recreating xorg with 

sudo dpkg-reconfigure xserver-xorg

and I have also tried various fixes found on the previous posts with 915resolution.

I know the card works with the screen because (as much as it pains me to say it)
 XP works at 1440x900 @75 mhz with the latest intel driver.

Here is my xorg.conf at present  The modeline was generate using gtf

any help greatly appreciated.

<<<<



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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"R19W12"
	Option		"DPMS"
 # 1440x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 136.49 MHz
  Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"R19W12"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900_75.00" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900_75.00"



	EndSubSection
EndSection

---

### Post by hectorkatz on 2007-11-12
one more thing...here is what i get with "sudo 915resolution -l"
i replaced mode 49 with 1440x900 with 16 bits

Now, I am getting 1440x900 resolution in the ubuntu menu under systems/screen resolution,
but there are still black bars on both sides of the screen and a brown line under the screen wallpaper at the bottom.  The right side of the dialogue boxes seems to be cut off...no "x" visible on the screen.

<<<

Chipset: 845G
BIOS: TYPE 3
Mode Table Offset: $C0000 + $4d2
Mode Table Entries: 25

Mode 30 : 640x480, 8 bits/pixel
Mode 31 : 640x400, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1440x900, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 40 : 640x480, 15 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 42 : 800x600, 15 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 44 : 1024x768, 15 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 48 : 1440x900, 15 bits/pixel
Mode 49 : 1440x900, 16 bits/pixel
Mode 4a : 1600x1200, 15 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4c : 1920x1440, 15 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1440x900, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

---

