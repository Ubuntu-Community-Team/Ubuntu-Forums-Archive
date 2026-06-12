---
title: "Big-Desktop configuration problems"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by edtechre on 2007-06-23
Hi all,

I just recently installed Ubuntu on my Dell 1501 laptop, and am trying to get dual monitors to work.  I followed the guide at [http://ubuntuforums.org/showthread.php?t=301941&page=1](http://ubuntuforums.org/showthread.php?t=301941&page=1) .  This works pretty well, as both monitors do show up. But I have 2 problems:

1.  I cannot get the display out of mirror mode (display is duplicated on both monitors)
2.  I cannot get the monitors to have their own individual resolutions.  Even putting:

Modes "1440x900" "1280x800"

In the screens section, I get 1440x900 on both.

Here's  /etc/X11/xorg.conf file.  My primary display is 1280x800, and external is 1440x900.  I'm thinking the problem is pretty simple, but as a complete novice, I'm stuck at this point.


```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
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
	Option	    "HorizScrollDelta" "0"
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

#Section "Monitor"
	#Identifier   "Generic Monitor"
	#Option	    "DPMS"
#EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1440x900+1280x800"
	Option	    "EnableMonitor" "lvds,crt1"
	Option 	    "Mode2"         "1440x900" #Resolution for secondm
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

#Section "Screen"
	#Identifier "Default Screen"
	#Device     "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	#Monitor    "Generic Monitor"
	#DefaultDepth     24
	#SubSection "Display"
		#Depth     1
		#Modes    "1280x800"
	#EndSubSection
	#SubSection "Display"
		#Depth     4
		#Modes    "1280x800"
	#EndSubSection
	#SubSection "Display"
		#Depth     8
		#Modes    "1280x800"
	#EndSubSection
	#SubSection "Display"
		#Depth     15
		#Modes    "1280x800"
	#EndSubSection
	#SubSection "Display"
		#Depth     16
		#Modes    "1280x800"
	#EndSubSection
	#SubSection "Display"
		#Depth     24
		#Modes    "1280x800"
	#EndSubSection
#EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Modes "1440x900" "1280x800"
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


PS If I get this working, I could add it to redDead's 1501 blog:
[http://ubuntu1501.blogspot.com/](http://ubuntu1501.blogspot.com/)

---

