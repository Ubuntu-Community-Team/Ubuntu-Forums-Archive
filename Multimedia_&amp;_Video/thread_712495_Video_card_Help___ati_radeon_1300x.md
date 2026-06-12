---
title: "Video card Help   ati radeon 1300x"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by zebo77 on 2008-03-01
I am trying to get my video card running... got a amd 64 processor 3.5   1ghz ram 

tried the forums for it....Its the visiontek Radeon 1300x series...no luck....its a pci slot add on used to work fine with windows just made the switch to linix. I did the whole install that was posted on the forums  [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
but when I try to verify that the install was correct this is what I get ...

fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

Segmentation fault (core dumped)

this is my current display settings
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "screen1" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
 #  
	Identifier   "monitor1"
	Gamma        1
EndSection

Section "Monitor"
 #  
	Identifier   "monitor2"
	Gamma        1
EndSection

Section "Monitor"
 #  
	Identifier   "monitor3"
	Gamma        1
EndSection

Section "Device"
 #  
	Identifier  "device1"
	Driver      "fglrx"
	BoardName   "OpenChrome"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
 #  
	Identifier  "device2"
	Driver      "radeon"
	BoardName   "VESA driver (generic)"
	Option	    "MergedFB" "off"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
 #  
	Identifier  "device3"
	Driver      "radeon"
	BoardName   "VESA driver (generic)"
	Option	    "MergedFB" "off"
	BusID       "PCI:2:0:1"
EndSection

Section "Screen"
 #  
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
EndSection

Section "Screen"
 #  
	Identifier "screen2"
	Device     "device2"
	Monitor    "monitor2"
	DefaultDepth     24
EndSection

Section "Screen"
 #  
	Identifier "screen3"
	Device     "device3"
	Monitor    "monitor3"
	DefaultDepth     24
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection



Also when I try to check restricted drivers it says its not enables and is in use..when I enable it and restart it......it just unables and I could do that 100xs and nothing. Someone please help me........

---

