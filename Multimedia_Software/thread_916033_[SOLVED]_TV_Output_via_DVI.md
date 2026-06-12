---
title: "[SOLVED] TV Output via DVI"
date: 2008-09-10
forum: Multimedia Software
---

### Post by jsnelli2 on 2008-09-10
Hey all,

I just bought a dvi to hdmi cable and am trying to configure x to allow for a cloned view onto my 27 inch tv.  Currently I've gotten the display up onto the TV, in what I assume to be a 1024x768 resolution.  My laptop monitor is running at 1920x1200.  The problem is the display on the TV is only the top left 1/4 of the screen (approximately).  I need to know how to make the entire display fit onto the TV monitor.  I will post my xrandr output and xorg file.  Any help is GREATLY appreciated. Thanks

> Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 2048 x 2048
VGA-0 disconnected (normal left inverted right)
DVI-0 connected 1024x768+0+0 (normal left inverted right) 400mm x 301mm
   720x480        59.9 +
   1024x768       74.9*    75.1     70.1     60.0  
   800x600        84.9     72.2     75.0     60.3     56.2  
   720x576        50.0  
   640x480        84.6     75.0     72.8     60.0  
LVDS connected 1920x1200+0+0 (normal left inverted right) 0mm x 0mm
   1920x1200      60.0*+
   1600x1200      59.9  
   1280x1024      59.9  
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right)


> Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"Generic Monitor"
	Option		"Monitor-DVI-0" "Mon-DVI"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc M22 [Mobility Radeon X300]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
     ...
	SubSection "Display"
	    Depth		24
            Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
            Virtual              2048 2048
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by jsnelli2 on 2008-09-11
Update:

I am able to get everything on the TV by running xrandr --output DVI-0 --mode 1024x768 and --output LVDS --mode 1024x768.  But these have to be run every time on boot and the second command is obviously reducing the resolution on my laptop monitor to 1024x768 from 1920x1200.  Is there any alternative to this? 

Also, I was having problems getting video to show up on the TV.  I was able to run mplayer with gl rendering getting it to show up on the TV, but Mplayer wants to crash when I close it and I am partial to Totem.  Is there anyway to change how Totem renders video?

---

### Post by jsnelli2 on 2008-09-19
Anybody have any ideas for me?  At least with the Mplayer problem?  Even though it's a pain to manually reduce the resolution on my laptop monitor so that I can have a full picture on the dvi, I at least can watch videos on the tv. (I would still like a multi resolution solution though)

---

### Post by jsnelli2 on 2008-09-29
Solved:

I was able to get an extended desktop exactly how I wanted after FINALLY getting the restricted ati drivers installed and running fglrx.

---

