---
title: "Dual monitor - Dual desktop. Why not?"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by leodp on 2007-03-09
Hi all,
sorry for starting over the same thing again.
I've read all the guides and posts on **xinerama**, **bigdesktop** & co., but cannot get it right.

I have a laptop with:
- a 1440x900 LCD
- an external monitor
Card is ATI Radeon 9600

I would like to run two independent desktops; I don't care if I cannot drag windows between them: I just need to play videos fullscreen on one monitor (generally the external) while at the same time working on the other monitor.

Let's say I start with this xorg.conf (I copy only the relevant part)
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "screen0" 0 0
	Screen         "screen1" RightOf "screen0"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection


Section "Monitor"
	Identifier   "LCD"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier  "ExtMonitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ati 0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ati 1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection



Section "Screen"
	Identifier "screen0"
	Device     "ati 0"
	Monitor    "LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1440x900"
	EndSubSection
EndSection

Section "Screen"
	Identifier "screen1"
	Device     "ati 1"
	Monitor    "ExtMonitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection



Section "DRI"
	Mode         0666
EndSection


```


Is there anyone that can tell me if my xorg.conf has problems?

---

### Post by Jake333 on 2007-03-11
Im in the same boat!  might as well get some :popcorn: Corn because no one seems to answer, try the freenode irc join #ubuntu or #ati if there is one and ask there also... ps if someone replys with the answer, please pm me the answer because ill be waiting :lolflag:    someday they will reply.......(thats ur cue u guru's)

---

### Post by scxtt on 2007-03-11
you're missing the "Screen 0" definition for the "ati 0" device, for starters ...

if you've already got fglrx working, try this xorg.conf on for size:
```
[font=courier]#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
       Identifier     "Default Layout"
       Screen      0  "aticonfig Screen 0" 0 0
       Screen      1  "aticonfig Screen 1" leftof "aticonfig Screen 0"
       InputDevice    "Generic Keyboard"
       InputDevice    "Configured Mouse"
EndSection

Section "Files"
       # path to defoma fonts
       FontPath     "/usr/share/X11/fonts/misc"
       FontPath     "/usr/share/X11/fonts/cyrillic"
       FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
       FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
       FontPath     "/usr/share/X11/fonts/Type1"
       FontPath     "/usr/share/X11/fonts/100dpi"
       FontPath     "/usr/share/X11/fonts/75dpi"
       FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
       Load  "bitmap"
       Load  "dbe"
       Load  "ddc"
       Load  "dri"
       Load  "extmod"
       Load  "freetype"
       Load  "glx"
       Load  "int10"
       Load  "record"
       Load  "type1"
       Load  "v4l"
       Load  "vbe"
EndSection

Section "InputDevice"
       Identifier  "Generic Keyboard"
       Driver      "kbd"
       Option      "CoreKeyboard"
       Option      "XkbRules" "xorg"
       Option      "XkbModel" "pc104"
       Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
       Identifier  "Configured Mouse"
       Driver      "mouse"
       Option      "CorePointer"
       Option      "Device" "/dev/input/mice"
       Option      "Protocol" "ExplorerPS/2"
       Option      "ZAxisMapping" "4 5"
       Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
       Identifier   "aticonfig Monitor 0"
       Option       "DPMS" "on"
       HorizSync    30-81
       VertRefresh  56-75
EndSection

Section "Monitor"
       Identifier   "aticonfig Monitor 1"
       Option       "DPMS" "on"
       HorizSync    30-80
       VertRefresh  50-75
EndSection

Section "Device"
       Identifier  "ATI Graphics Adapter 0"
       Driver      "fglrx"
       Option      "(null)"
       Option      "VideoOverlay" "on"
       Option      "OpenGLOverlay" "off"
       Option      "DesktopSetup" "horizontal"
       Option      "UseInternalAGPGART" "off"
       BusID       "PCI:1:0:0"
       Screen      0
EndSection

Section "Device"
       Identifier  "ATI Graphics Adapter 1"
       Driver      "fglrx"
       BusID       "PCI:1:0:0"
       Screen      1
EndSection

Section "Screen"
       Identifier "aticonfig Screen 0"
       Device     "ATI Graphics Adapter 0"
       Monitor    "aticonfig Monitor 0"
       DefaultDepth     24
       SubSection "Display"
#               Virtual   1600 1200
#               Viewport   0 0
               Depth     24
               Modes     "1600x1200"
       EndSubSection
EndSection

Section "Screen"
       Identifier "aticonfig Screen 1"
       Device     "ATI Graphics Adapter 1"
       Monitor    "aticonfig Monitor 1"
       DefaultDepth     24
       SubSection "Display"
#               Viewport   0 0
               Depth     24
               Modes     "1360x768"
       EndSubSection
EndSection

Section "DRI"
       Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection[/font]
```now obviously you CAN'T just copy and paste this for immediate results ... but my config is as follows:

20" samsung LCD @ 1600x1200
32" westinghouse TV @ 1366x768
ATI x850pro

and it will hinge on fglrx (and associated tools) being installed and working ...

---

