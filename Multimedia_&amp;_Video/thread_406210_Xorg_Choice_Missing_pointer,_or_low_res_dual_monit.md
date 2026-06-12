---
title: "Xorg Choice: Missing pointer, or low res dual monitor setup (MergedFB question )"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by centavo on 2007-04-10
Weird one that i've been banging my head on for a few hours...

This is what i'm trying to setup.

I want to mirror a laptops lcd display on an external lcd, so both screens display the same thing. But, the laptop supports a lower resolution than the exterior display. The two options are, run both at the lower resolution, or run the laptop at a virtual resolution ( ie, where you have to use the mouse to "scroll" around the screen). I've gotten both working.

The issue is, that when i use the virtual resolution on the laptop lcd, the external monitor doesnt display the cursor.

The external display's max resolution is 1680x1050, the laptop can only support 1280x800.
Laptop is a T60, using the built in intel graphics 945, and the i810 driver.

So with one config, i can do all of this using MergedFB, BUT.. the pointer is missing on the external monitor. All actions register, but the pointer isnt on the external screen ( it is on the laptop).

WIth the other config, using the standard clone setup, i can get a simple clone wich means the mouse shows up in both places, but both screens running at the same lower resolution.

And yes, i have read the sticky on the forum. It isnt doing much, the issue is not the dual display. the issue is the non viewable pointer on the external LCD.

( just in case, its a dell E228WFP )


===== high res external, no mouse external ====

Section "ServerLayout"
	Identifier     "Dual layout"
	Screen      0  "LaptopScreen" 0 0
	Screen      1  "ExternalScreen" 0 0
	InputDevice    "Synaptics" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice     "Synaptics" "SendCoreEvents"
	Option	    "Xinerama" "true"
	Option	    "Clone" "true"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Synaptics"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "auto-dev"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Device"
	Identifier	"Intel 945 Graphics Controller LaptopScreen"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Option  "Clone" "true"
        Option "DRI"      "true"
        Option "MergedFB"      "true"
        Option "MergedXinerama" "true"
        Option "OverlayOnCRTC2" "true"
        Option          "DevicePresence" "true"
        Option          "CheckLid" "false"
	Screen          0
EndSection

Section "Device"
	Identifier	"Intel 945 Graphics Controller ExternalScreen"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen          1
EndSection

Section "Monitor"
	Identifier	"InternalLCD"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"ExternalLCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier "LaptopScreen"
	Device     "Intel 945 Graphics Controller LaptopScreen"
	Monitor    "InternalLCD"
	DefaultDepth     24
	Option 	"SWCursor"  "1"
	SubSection "Display"
		Depth     24
	 	Modes      "1280x800"
	 	Virtual    1680  1050
	EndSubSection
EndSection
Section "Screen"
	Identifier "ExternalScreen"
	Device  "Intel 945 Graphics Controller ExternalScreen"
	Monitor    "ExternalLCD"
	DefaultDepth     24
	Option 	"SWCursor"  "1"
	SubSection "Display"
		Depth     24
	 	Modes      "1680x1050"
	EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

=====end ===




=== low res both monitors

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen        "LaptopScreen" 
	InputDevice    "Synaptics" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice     "Synaptics" "SendCoreEvents"
	Option	    "Xinerama" "true"
	Option	    "Clone" "true"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Synaptics"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "auto-dev"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Device"
	Identifier	"Intel 945 Graphics Controller LaptopScreen"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Option "DRI"      "true"
	Option	    "Clone" "true"
EndSection

Section "Monitor"
	Identifier	"InternalLCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier "LaptopScreen"
	Device     "Intel 945 Graphics Controller LaptopScreen"
	Monitor    "InternalLCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	 	Modes       "1280x800" 
	EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection
=== end===

---

