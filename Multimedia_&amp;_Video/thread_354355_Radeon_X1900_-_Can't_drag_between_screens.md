---
title: "Radeon X1900 - Can't drag between screens"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by mr9times on 2007-02-05
Hi,
I've spent the day reading the forums here and elsewhere trying to get my dual-head system working and I've had partial success thanks to the information I found here. I do have both monitors working and am able to control the resolutions and refresh rates just fine. The last thing that isn't working is being able to drag windows between screens and treat the 2 monitors as one big desktop. (They behave as 2 completely separate entities with their own top and bottom bars [dunno what they're called] and their own workspace switcher panels [that are unaware of apps running on the other monitor].)

I have tried most of the suggestions I found in these forums to no avail.

I am running Edgy 64-bit, Radeon X1900, and ATI drivers. I installed the drivers following these instructions: 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2)


Here are the pertinent pieces of my xorg.conf:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
#	InputDevice    "stylus" "SendCoreEvents"
#	InputDevice    "cursor" "SendCoreEvents"
#	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
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

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
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


Thanks.

---

### Post by Schluppy on 2007-02-05
You need to enable the *xinerama* extension. A search of the forums here should give you everything you need to know to configure it.

---

### Post by mr9times on 2007-02-06
Thanks, Schluppy. 
I ran through Ziox's tutorial [_here_]("http://www.ubuntuforums.org/showthread.php?t=301951") and one issue is solved and two new issues cropped up.

I am able to drag windows between screens but am unable to control the resolution or refresh on screen 0 (screen 1 works). It's set to some outrageously high resolution and low refresh. 

Also, my cursor on screen 1 is just a big square with garbled image in it.

Here are the new xorg.conf sections regarding video:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         0 "aticonfig-Screen[0]"
	Screen         1 "aticonfig-Screen[1]" RightOf "aticonfig-Screen[0]"
	Option         "Xinerama" "true"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      0
	Option      "DDCMode" "True"
	Option      "MonitorLayout" "CRT,CRT"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
	Option      "DDCMode" "True"
	Option      "MonitorLayout" "CRT,CRT"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Modes     "1280x960"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Modes     "1152x864"
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

---

### Post by Schluppy on 2007-02-07
Check out the xorg.conf manpage ("*man xorg.conf*" from a terminal). There are directives to set both vertical and horizontal refresh ranges in the *monitor* sections of xorg.conf. It may be worth setting the *DisplaySize* directive as well.

In addition, have a look at your X log (*/var/log/Xorg.0.log*). If setting the refresh ranges manually doesn't fix the issue post your log. Most oddities are readily apparent in the log.

---

