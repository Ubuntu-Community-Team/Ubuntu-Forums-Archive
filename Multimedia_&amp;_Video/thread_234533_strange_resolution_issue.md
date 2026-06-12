---
title: "strange resolution issue"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by jaredvolkl on 2006-08-11
This one has me stumped. I left work yesterday, locked my workstation as usual. I came in today and apparently, the power had flickered overnight and the PC shut off. After boot, things were amiss.

Previous to today, I was using a resolution of 1280x1024 @ 60Hz just fine.

Now, the resolution still shows 1280x1024, but I've only got a virtual screen size of 1024x768. From my days messing around with old hardware and X, this sounds like the concept of virtual resolutions. The idea is you can use a larger resolution than the monitor supports. When the mouse reaches the edge of the screen, it slides over to reveal the rest of the desktop. This is exactly what it is doing, but I haven't enabled it in my xorg.conf. In fact, nothing in the conf should've changed at all between last night and today.

Via the monitor OSD, I found  that it's currently running at 85Hz. This leads me to believe that it is indeed running in 1024x768 with the 1280x1024 as the virtual size because the monitor, I know, doesn't support 1280x1024 @ 85Hz.

So far I've tried many different solutions without luck including sudo dpkg-reconfigure xserver-xorg, setting a modeline in the conf, trying the ViewPort keyword in conf. None of them changed anything. 

I'll also note that this is a Dell Optiplex 170L so I'm using an Intel graphics chip which brought some headaches during setup. I was stuck in 640x480. After bumping the VRAM from 1MB to 8MB in the BIOS and setting the Horiz and Vert refresh rates in my xorg.conf, the problem was fixed though.

Below you'll find my current xorg.conf file

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"AVITRON"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-100
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"AVITRON"
	DefaultDepth	24
#	SubSection "Display"
#		Depth		1
#		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		4
#		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		8
#		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		15
#		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		16
#		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
#	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by jaredvolkl on 2006-08-14
Bump.

---

