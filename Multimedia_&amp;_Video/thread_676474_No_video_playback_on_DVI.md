---
title: "No video playback on DVI"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by tech.roberts on 2008-01-23
Gutsy with an ATI Technologies Inc RV280 [Radeon 9200 PRO] video card using the open source drivers.  Card has a VGA and A DVI port (dual head) Compiz with cube and other eye candy is working fine. Rotating gears eye candy works fine.   glxinfo reports vendor sting as:
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

Direct rending is working:  glxinfo | grep "direct rendering":
direct rendering: Yes

Problem: If i use the DVI port to a DVI montor all is well except no video playback of any kind just  sound.  (No DVD playback either)  Video playback screen or area is blueish with sound present but no video. If I use the VGA port even to the same monitor (Viewsonic VA912b) video playback, including DVD's  is fine.

Behavior is consistent no matter what application I use to play back video or DVD's.

Any suggestions?  Here is my xorg.conf:

```
Section "Extensions"
	Option		"Composite"	"Enable"
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

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option		"DPMS"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
	Option	   "XAANoOffscreenPixmaps"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier     "Default Layout"
        Screen          "Default Screen"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection
```

---

### Post by tech.roberts on 2008-01-29
This one still remains unsolved.  I discovered a workaround that other's may find useful.  If I start X with the VGA cable unplugged then the problem is resolved. Once X is started I can  plug the VGA back in and the problem is gone.  If I restart X though with both ports attached the problem returns.

---

