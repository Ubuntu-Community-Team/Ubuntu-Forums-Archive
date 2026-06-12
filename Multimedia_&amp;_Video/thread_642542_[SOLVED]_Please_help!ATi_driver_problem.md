---
title: "[SOLVED] Please help!ATi driver problem"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by Tarmael on 2007-12-16
Hey, I'm sure there has been similar problems in other threads, but my problem is too defined to search for it.

I've got the ATi 8.433 driver installed, however I run fglrxinfo and it comes up with 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.1.7059 Release

Then I run glxinfo and it comes up with 
name of display: :1.0
display: :1  screen: 0

with
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

The biggest difference I've seen is the ATi Display 0.0 on screen 0 and glx display 1.0 on screen 0.

So to me it says I've got display 1 as default and display 0 never running.

How do I change it?

should I comment out load glx from my xorg.conf?

Cheers,
Basil.

---

### Post by Tarmael on 2007-12-17
I've now tried turning off glx in xorg.conf, I don't think that did anything.

I've been searching through the forums too for a bit, can't find anything to help me as of yet, still hoping someone replies.

---

### Post by Tarmael on 2007-12-17
Easier way of showing what my problem is.

tarmael@melchior:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

tarmael@melchior:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.1.7059 Release

---

### Post by Tarmael on 2007-12-17
So has no one had this same problem before?

Am I talking to myself here? It would really benefit me to have these drivers working properly as so I wouldn't have to boot to Windows every time I want to game.

Effectively, this is a bump.

---

### Post by Tarmael on 2007-12-17
*sigh* Bump.

Nothing new as of yet.

---

### Post by Presto123 on 2007-12-18
FYI: Any changes to your display settings probably will not affect it right off. You will have to save it to your X config file and then reboot. A word of warning, though, don't get over zealous and try to turn off the working one at any point, because you will probably loose a way to see what you're doing.

---

### Post by Yellow Pasque on 2007-12-18
Please post your etc/X11/xorg.conf and let's see whats's going on.

---

### Post by Tarmael on 2007-12-18
> **Presto123 said:**
> FYI: Any changes to your display settings probably will not affect it right off. You will have to save it to your X config file and then reboot. A word of warning, though, don't get over zealous and try to turn off the working one at any point, because you will probably loose a way to see what you're doing.

I do know about having to restart the xserver after any changes, yes.
I also know how to use nano right, and not to bother turning off my drivers... That would just be unwise. I'm a patient person.

> **Temüjin said:**
> Please post your etc/X11/xorg.conf and let's see whats's going on.

Righto.

```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dri"
	Load  "glx"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
	Option      "TexturedXrender" "true"
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

```

---

### Post by Yellow Pasque on 2007-12-18
Add this to the end of your file:
```
Section "DRI"
	Mode 0666
EndSection
```

- Also, try turning OpenGL overlay off.

- And it might help to explicitly point X to your video card. First, get your PCI ID with:
```
sudo update-pciids
lspci | grep VGA
```
Then, add the BusID "PCI:x:y:z" line to your Device section, substituting your PCI ID.
Example: Mine says "01:05.0 VGA compatible controller: ATI Technologies Inc RS690", so the line in my xorg.conf Device section says BusID "PCI:1:5:0"

---

### Post by Tarmael on 2007-12-19
Hey.

I've tried those suggestions, my problem persists.

Cheers,
Basil.

---

### Post by Tarmael on 2007-12-21
Fixed.

I didn't realise that Ubuntu installed xgl by default.

Got rid of that, and it works.

Cheers,
Basil.

---

