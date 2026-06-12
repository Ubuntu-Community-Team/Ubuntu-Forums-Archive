---
title: "fglrx, dualhead, and dri"
date: 2006-05-23
forum: Multimedia &amp; Video
---

### Post by canadabear on 2006-05-23
I and/or Xorg.conf is a little confused; xorg.conf reports that my monitor is on my mobo video, an i810 intel chip. However, my monitor is definetly plugged in to a PCI radeon 9200SE! Does this mean i am not using the correct drivers? i would ultimately like to use whatever is fastest for the ATI card, and maybe dualhead with another monitor plugged in to the i810 (if possible). 
To clarify, i currently only have one monitor which is connected to the ATI card.

Additionally, when i run fglrxinfo and some other graphics programs, they complain: "Xlib:  extension "XFree86-DRI" missing on display ":0.0"."
xdriinfo output:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Screen 0: not direct rendering capable.

does that mean that my monitor/video setup does not support dri, or is it something on the software end? (monitor = Dell E151FPb)

xorg.conf:
...
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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:1:4:0"
EndSection

Section "Monitor"
	Identifier	"DELL E151FPb"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics
...
Section "DRI"
	Mode	0666
EndSection

Thank you for your assistance.

---

