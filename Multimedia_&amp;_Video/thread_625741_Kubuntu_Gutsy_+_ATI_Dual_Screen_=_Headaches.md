---
title: "Kubuntu Gutsy + ATI Dual Screen = Headaches"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by ayapejian on 2007-11-28
Hey Everyone ... So heres the deal ... I have an IBM Thinkpad T60 with the ATI X1400 card, I'm trying to get the laptop screen AND external LCD monitor working via a docking station.  Before I started everything worked perfectly on the laptop monitor only, had good frame rate for glxgears, had direct rendering working, etc... (No compiz yet, haven't gotten that far).  

Now I wanted to get dual monitors working at my office so I got that all configured and the resolutions look good (1400x1050, and 1600x1200) the problem comes in with speed and "artifacts" appearing.  glxgears reports only about 900fps, was at about 3400fpx before on single screen, direct rending is listed as not found, and when I drag windows around the screen doesn't refresh all the time, so I have little reminents of past windows, or icons, or mouse curso, laying around the screen until I drag something over it and it forces a redraw. 

I've looked everywhere for some help, can't find anything (even though I know this is a highly covered topic) ... the external monitor is a Samsung SyncMaster 204B.  Please find the copy of xorg.conf as well as other possibly relevent information below.

Thanks for any help you can provide!

```

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Laptop LCD Screen" 0 0
	Screen         "External LCD Screen" LeftOf "Laptop LCD Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	Option		"Xinerama"	"on"
	Option		"Clone"		"off"
EndSection

Section "Files"
EndSection

Section "Module"
	#Load  "glx"
	Load  "dri"
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
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
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
	Identifier   "Laptop LCD Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "External LCD Monitor"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI X1400 (Head 1 - Internal)"
	Driver      "fglrx"
	Option "SWCursor" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI X1400 (Head 2 - External)"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Laptop LCD Screen"
	Device     "ATI X1400 (Head 1 - Internal)"
	Monitor    "Laptop LCD Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "External LCD Screen"
	Device     "ATI X1400 (Head 2 - External)"
	Monitor    "External LCD Monitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "disable"
EndSection

```

```

ayapejian@ayapejian-T60:~$ glxinfo | grep vendor
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Mesa project: www.mesa3d.org

```

```

ayapejian@ayapejian-T60:/var/log$ grep -A 5 -B 5 EE /var/log/Xorg.0.log
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(EE) AIGLX: Screen 1 is not DRI capable
(II) GLX: Initialized MESA-PROXY GL provider for screen 1
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!

```

```

ayapejian@ayapejian-T60:/var/log$ lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

```

---

### Post by ayapejian on 2007-11-28
No help?  Someone has got to have run into this?

---

