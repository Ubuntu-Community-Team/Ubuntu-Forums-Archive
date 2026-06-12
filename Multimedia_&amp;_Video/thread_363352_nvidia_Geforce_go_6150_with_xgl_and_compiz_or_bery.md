---
title: "nvidia Geforce go 6150 with xgl and compiz or beryl problem!"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by lien_meat on 2007-02-16
I have a Compaq Presario V3015nr laptop running dapper 64bit.
I would love to get compiz or beryl working on it, but I believe that the video card makes it near impossible.

The problem I'm getting is when I try to start XGL with Gnome, I get:

$ compiz.real: GLX_EXT_texture_from_pixmap is missing
$ compiz.real: Failed to manage screen: 0
$ compiz.real: No managable screens found on display :0.0

It's odd because I can still see some things. Windows stay open, but the titlebars and taskbar goes away, and I can't seem to use my normal shortcuts to get to the terminal or anything.

System Hardware in question:
CPU: Turion 64 X2
Video: Nvidia Geforce Go6150

My /etc/X11/xorg.conf looks like:

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
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
	Identifier	"NVIDIA GEFORCE go 6150"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	Option "RenderAccel" "true"
 	Option "AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GEFORCE go 6150"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x800" "1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
   Option "Composite" "Enable"
 EndSection

```

I've already jumped through hoops to get my bmc4311 wifi card working, and my headphone jack on the hda-intel sound card working correctly, which is why I'm running dapper 64bit.  It's the only kernel that seems to work with everything.  32bit refuses to let my headphone jack work, and Edgy seems to be incompatable with my wifi.

I believe the problem lies with the BusID of my card.  All the tutorials for xgl+compiz or beryl show in the xorg.conf that BusID is PCI:1:0:0, however, my card only works with the BusID set to PCI:0:5:0.

I believe I have everything I need installed for xgl and compiz.  I've done a lot of work ensuring this...but I'm not sure.

If anyone could provide ANY insight, that would be awesome.  If you have any questions on laptops with hardware similar to this, I probably have some pretty good answers...so ask.

---

### Post by coolen on 2007-02-20
If you're okay using beta drivers, you can get it running with AIGLX. No need for seperate sessions: I often just fire up Beryl after an hour or so when I get bored.
XGL worked like a charm for me, using the instructions in the Beryl Wiki. Only problem I had was my GTK theme going to an ugly default, but there were useful troubleshooting tips down the bottom.

---

### Post by coolen on 2007-02-20
Ooh, sorry, just read your distro. AIGLX is supported in Edgy. You can probably get it in Dapper with some additional upgrades, but not outright, I don't think.

---

### Post by onlybui on 2007-02-23
Follow these instructions I got same hardware but I have HP dv9000tz and it it working....

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia#Automatic_installation)

---

