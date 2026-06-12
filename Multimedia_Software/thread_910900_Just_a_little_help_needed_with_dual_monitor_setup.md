---
title: "Just a little help needed with dual monitor setup"
date: 2008-09-05
forum: Multimedia Software
---

### Post by winrowc on 2008-09-05
I have two old crt monitors and have been trying to get a desktop to spread across the both of them in Ubuntu 7.1. I have a radeon 9600 video card and went the MergedFB route in terms of trying to setup the desktop. I went into the ATi video card manager (Im using the ati drivers that i installed with "Envy") and switched the desktop to big desktop, where it shows the picture of the fish across the two screens, and I enabled the other monitor. This  restarted the xserver, and I had to log back in, but its only a single screen still. I was not able to get the clone option to work either, though I have in the past before I tried anything with MergedFB. First I thought this was because either the other monitor was not working or it was out of range, but it shows the ubuntu logo and loading bar at start up, and it used to show a Sync out of range when it was out of range before. This time I got the vertrefresh and horizsync values correct so Im at a loss for what is left to do. Is it something to do with using ATI drivers? Cause isn't it spose to make it think its one big screen? Any help would be appreciated. 

Here's my xorg.conf file:
```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
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
	Identifier   "Generic Monitor"
	Horizsync    28-64 #You may wish to change the values to fit your specific monitor
    	Vertrefresh    43-60
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"

EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "clone"
	Option	    "EnableMonitor" "crt2"
	Option "MergedFB" "true" #Enable MergedFB function
	Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
	Option "CRT2Hsync" "30-85" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option "CRT2VRefresh" "50-160" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	Option "OverlayOnCRTC2" "true"
	Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: 			LeftOf, RightOf, Above, Below, and Clone.
	Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
	#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or 		"false"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "01:00:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RV350 AP [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

---

### Post by winrowc on 2008-09-05
Hmm, now its also not letting me add desktop effects, even though my video card is clearly capable and was able to before editing xorg.conf...

---

### Post by winrowc on 2008-09-06
Ubuntu also shows just two really wide screens, in the screen switching thing in the bottom right. Apparently I'm just using half of the screen, but the task bars are not spread out, and the other screen is still blank. Can anyone help?

---

### Post by blogsarticle on 2008-09-06
Can anyone help?[COLOR="White"][.]("http://www.blogsarticle.com")[/COLOR]

---

