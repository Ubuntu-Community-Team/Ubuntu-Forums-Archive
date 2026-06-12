---
title: "nvidia Inspiron 9300: External Monitor Only when plugged in, laptop when not?"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by ledneh on 2006-08-07
I tried really hard to be succinct with the title, but there was just no good way. Sorry.

In Windows I used Ultramon so that I could plug in my external monitor, and change modes so that my laptop monitor turned off and windows changed to 1280x960 on the external. When I was done, I could tell Ultramon to turn off the external, and go back to the laptop at 1920x1200. 

I also had a profile for stretching across both monitors, but I rarely used it. I've got the equivalent for this working using Xinerama and google, but frankly figuring out Xinerama, Twinview, or whatever the hell all my options are is frustrating the hell out of me. Google isn't helping much.

Can anyone point me to where I might look to set it up like I had it in Windows, such that when plugged in it displays at 1280x960 on the external and shuts off the laptop monitor, and 1920x1200 on the laptop monitor when unplugged?

Here's my current xorg.conf, for reference. This works across the two monitors, but that's not really what I want, as I mentioned.

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
	Identifier	"video device"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen 0
	Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
	Identifier	"video device 2"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen 1
	Option "MonitorLayout" "CRT,LFP"
EndSection

Section "Monitor"
	Identifier	"laptop monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier "desktop monitor"
	Option "DPMS"
EndSection

Section "Screen"
	Identifier	"laptop screen"
	Device		"video device"
	Monitor		"laptop monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"desktop screen"
	Device		"video device 2"
	Monitor		"desktop monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x960"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960"
	EndSubSection
EndSection

#Section "ServerLayout"
#	Identifier	"Default Layout"
#	Screen		"Default Screen"
#	InputDevice	"Generic Keyboard"
#	InputDevice	"Configured Mouse"
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
#	InputDevice	"Synaptics Touchpad"
#EndSection

Section "ServerLayout"
	Identifier "Two Monitors"
	Screen 0 "desktop screen" 0 0
	Screen 1 "laptop screen" rightof "desktop screen"
	Option "Xinerama" "On"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Thanks!

---

### Post by ledneh on 2006-08-08
Bump. Anyone?

---

### Post by tseliot on 2006-08-11
> **ledneh said:**
> Can anyone point me to where I might look to set it up like I had it in Windows, such that when plugged in it displays at 1280x960 on the external and shuts off the laptop monitor, and 1920x1200 on the laptop monitor when unplugged?
I don't know if this can be done. I think that you'll have to set the resolution manually.

P.S. I'm moving this thread to the Video & sound section

---

