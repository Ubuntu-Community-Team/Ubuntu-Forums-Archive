---
title: "XGL - Need help for this weird error please"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by syuusuke on 2006-06-07
I tried googling it, asking on IRC, searching on forums but no luck.  I just ask everywhere but seems like they have no answer or they just avoid my question. 

I followed the [tectonic]("http://www.tectonic.co.za/view.php?id=916") xgl tutorial guide and this is the error that I got.  Xgl and Compiz runs fine, none of those errors when trying to log in.  I could log in to XGL session but its really slow when opening applications even terminal.   Their isn't any effects showing up when dragging windows, actually there arent any effects at all for any windows.

Error:
```

Xlib: extension "XFree86-DRI" missing on display":1.0"
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5755 (8.24.8)

```

here is my xorg.conf file
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
#	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseInternalAGPGART" "no"
	Option	    "KernelModuleParm" "agplock=0"
	Option	    "no_accel" "no"
	Option	    "no_dri" "no"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
#	Group	     Video
EndSection

```

Anyone have a solution to this problem?  Or is this thread going to be avoided once again? ](*,)

---

### Post by syuusuke on 2006-06-08
bump

---

### Post by viz_e on 2006-06-09
Same problem here after enabling xinerama...

---

### Post by _Zardoz_ on 2006-06-09
Same problem here, but the entire environment is fast...strange thing. Ati x600 mobility.

---

### Post by Aurelias on 2006-06-09
I've been running Xgl+compiz for a few days now after getting it up and running with the [ubuntu-oriented tutorial]("https://wiki.ubuntu.com/CompositeManager/Xgl").  Maybe if you tried using the latest official kernel/fglrx packages from Universe/Multiverse/wherever they are?  I'm using the 8.25.18 drivers, but tried a while ago with the 8.23.yadda ones and couldn't get anything to work.

Hope something helps,
Aurelias

---

### Post by Aurelias on 2006-06-10
I did the following this morning ```
> glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
...
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 1.2 (2.0.5814 (8.25.18))
```
And this is with xgl+compiz working just fine (quinnstorm packages).  Maybe it's something to do with how xgl works?  But if that was the case, you'd think it would work fine for you, too.
-Aurelias

---

### Post by syuusuke on 2006-06-10
[QUOTE=Aurelias]I've been running Xgl+compiz for a few days now after getting it up and running with the [ubuntu-oriented tutorial]("https://wiki.ubuntu.com/CompositeManager/Xgl").  Maybe if you tried using the latest official kernel/fglrx packages from Universe/Multiverse/wherever they are?  I'm using the 8.25.18 drivers, but tried a while ago with the 8.23.yadda ones and couldn't get anything to work.

Hope something helps,
Aurelias[/QUOTE]

YES! thank you!  that link you provided me worked perfectly on the first try! :D  I used the packages from Quinn and its working very good.  man this interface is slick!  So to wrap it up, what I did was to follow the tutorial link above and updated my ATI drivers to 8.25.18.   And if your curious on what the specs on my laptop, google compaq V2410CA.  It's a 200M ATI mobile.

Oh and a final note,  I used method A for XGL and method B for compiz tutorial.

---

