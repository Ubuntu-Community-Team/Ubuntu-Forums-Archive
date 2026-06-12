---
title: "ATI Driver problem, still Mesa"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by traeskapa on 2007-09-03
Hello there!
I have installed and uninstalled fglrx over and over again, following every guide I could find, and still my fglrxinfo says Mesa.
I'm running Xubuntu 7.04 with a ATI x1600 Pro.
I got it working in Debian before, but it seems like it's refusing to work with fglrx in Xubuntu 7.04.

This is how my xorg.conf looks at the moment.
Please, if anyone got anything to help, speak up!
I'm tired of Mesa :/

I tried Envy now, and after that, my fglrxinfo now outputs:
```

Xlib: extension "XFree86-DRI" missing on display ":0.0".
And then the usual Mesa-thingy.

```

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
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
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection



```

---

### Post by phreadom on 2007-09-03
I also have GLcore in my "Module" section and the following at the end of my xorg.conf:

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

With those, I get DRI working on here.

---

### Post by traeskapa on 2007-09-03
phreadom;
I tried with that, but still, Mesa is there, ruining the party.
Mesa is such a party pooper.

---

### Post by traeskapa on 2007-09-03
Well, for some reason I got it working.
I uninstalled all fglrx-things, and installed it directly with ATI's script, and it worked.
Very weird, since I've done that like 5 times already.
But, yay, it works!

---

### Post by sdowney717 on 2007-09-03
did you ever use ENVY?

---

### Post by traeskapa on 2007-09-04
sdowney717: Yes, and it didn't work for me.

---

### Post by ressac on 2007-09-04
please tell me where to get this script? 
thx

---

### Post by traeskapa on 2007-09-05
> **ressac said:**
> please tell me where to get this script? 
thx

Well, I just meant the ATI-installer that you get from [www.ati.com](www.ati.com).
That was the one I ran, and then it suddenly worked.

---

### Post by kellemes on 2007-09-05
> **traeskapa said:**
> phreadom;
I tried with that, but still, Mesa is there, ruining the party.
Mesa is such a party pooper.

Actually Mesa saves a lot of buts of those not being able to install there preferred driver. :popcorn:

The only thing you needed to do was install xgl. The magic potion is fglrx+xgl.
Glad it works.

---

