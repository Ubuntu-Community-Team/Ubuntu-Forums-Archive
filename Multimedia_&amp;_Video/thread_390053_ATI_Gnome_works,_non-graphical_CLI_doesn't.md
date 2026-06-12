---
title: "ATI: Gnome works, non-graphical CLI doesn't"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by AZzKikR on 2007-03-21
I have Ubuntu Edgy Eft installed as of err... well two weeks after it was released. Besides the usual problems I already knew I was going to have, it installed find and dandy. Been working with it since then, and no complaints really :D

However, one little thing is bugging me. I have a ATI Radeon X800/850, and I can play OpenGL enabled games very well: UT2k3, Neverwinter Nights, you name it. Switching to the command line interface while in Gnome using CTRL+ALT+F1 through F6 gives me weird artifacts on my screen. I can switch back perfectly to Gnome using CTRL+ALT+F7.

I don't know really where to look for the problem, nor the solution on this forum. See the attached screenshot how my screen looks like. I think the problem lies somewhere in my xorg.conf configuration.

Some output data for information:

**$ cat /etc/X11/xorg.conf**
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
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
	Option	    "XkbVariant" "intl"
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
	HorizSync    28.0 - 51.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon X850 Pro (R480)"
	Driver      "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X850 Pro (R480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1152x864" "1024x768" "800x600"
	EndSubSection
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
	Option	    "Composite" "Disable"
EndSection


```

**$ fglrxinfo:**
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

Any hints, tips, or even solutions to this matter will be greatly appreciated. :)

---

### Post by Belyel on 2007-03-21
For what it's worth, I have the same problem.  Are you running beryl on XGl, by chance?  Does this problem occur even when you are on the login screen? Edit: I just logged out to test this, and mine does the weird artifacty thing from the login screen, too.  I'm running beryl on xgl, but from the login screen that shouldn't matter.  here's my xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
#	InputDevice    "stylus" "SendCoreEvents"
#	InputDevice    "cursor" "SendCoreEvents"
#	InputDevice    "eraser" "SendCoreEvents"
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
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dbe"
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
	Identifier     "Synaptics Touchpad"
    	Driver         "synaptics"
    	Option         "SendCoreEvents" 	"true"
    	Option         "Device" 		"/dev/psaux"
    	Option         "Protocol" 		"auto-dev"
	Option	       "HorizScrollDelta"	"0"
	Option	       "SHMConfig" 		"on"
EndSection

#Section "InputDevice"

                                                      # /dev/input/#event
                                                      # for USB
#	Identifier  "stylus"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "stylus"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC #ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/#event
                                                      # for USB
#	Identifier  "eraser"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "eraser"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC #ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/#event
                                                      # for USB
#	Identifier  "cursor"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to #
#	Option	    "Type" "cursor"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC #ONLY
#EndSection

Section "Monitor"
	Identifier   "ACER LCD"
	HorizSync    30.0 - 90.0
	VertRefresh  50.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Ic. x1600m"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Ic. x1600m"
	Monitor    "ACER LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


```

---

### Post by AZzKikR on 2007-03-21
Thanks for the reply. No I do not have Beryl running, just plain X with gdm.

I logged in safe-boot mode, fiddled with the xorg.conf file, started GDM and it booted alright. I could switch using ctrl+alt+f1 to my original CLI, and I could switch back. However, when rebooting, straight into GDM, ctrl+alt+f1-6 still give me the artifacts. 

I wonder whats going on.

---

### Post by Belyel on 2007-05-10
Bumping this!  Still having the problem and searching the forums is fruitless thus far.

---

