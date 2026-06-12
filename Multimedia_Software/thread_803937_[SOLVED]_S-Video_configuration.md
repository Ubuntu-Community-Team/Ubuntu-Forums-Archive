---
title: "[SOLVED] S-Video configuration"
date: 2008-05-22
forum: Multimedia Software
---

### Post by gekkoo on 2008-05-22
Hello,

I've already searched in this forum and everywhere else but couldn't find a solution for my problem. 

First up my graphic card is ATI Mobility Radeon 7500.

I've bought a S-Video -> Scart Cable/Adapter to connect my laptop with my TV. First I've tested it on Windows - everything worked, even the picture was colored.
On Linux it doesn't work if I try it through the xorg.conf. If I use atitvout or xrandr (A tool to activate the S-Video out) it works, but I get only a black-white picture

Now I want to try to configure it through xorg.conf. Hier is my config:
```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option      	"Emulate3TimeOut"     	"50"
	Option      	"EmulateWheel"        	"on"
	Option      	"EmulateWheelTimeOut" 	"200"
	Option      	"EmulateWheelButton"  	"2"
	Option      	"YAxisMapping"        	"4 5"
	Option      	"XAxisMapping"        	"6 7"
	Option      	"ZAxisMapping"        	"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen 0
        #Option "XAANoOffscreenPixmaps" "true"
EndSection

Section "Device" 
   Driver          "vesa" 
   Identifier      "Device[1]" 
   Screen 1 
   Option          "TVOutFormat" "SVIDEO" #or SVIDEO etc 
   Option          "TVStandard" "PAL-B" #or NTSC, PAL-I for uk etc 
   Option          "ConnectedMonitor" "Monitor[1]" 
   BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Monitor"
	Identifier	"Monitor[0]"
	Option		"DPMS"
EndSection

Section "Monitor" 
   Identifier "Monitor[1]" #TV 
   HorizSync 30-95
   VertRefresh 60
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
		ViewPort	0 0
	EndSubSection
EndSection

Section "Screen" 
	Device "Device[1]" 
	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
       	SubSection "Display" 
               Depth 24 
               Modes "1024x768" 
       	EndSubSection    
EndSection

Section "ServerLayout"
	Identifier  "Simple Layout" 
   	Screen "Screen[0]" 
        Screen 1 "Screen[1]" RightOf "Screen[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

```
In the Device Section for my TV I've to use the vesa driver else (if I use the ati drivers) I get the following error message:
```

Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux debian 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 22 23:54:36 2008
(==) Using config file: "/etc/X11/xorg.conf"

(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
NTSC PAL NTSC-J 
finished output detect: 0
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
NTSC PAL NTSC-J 
=====>>>>> (EE) RADEON(1): Invalid TV Standard: PAL-B <<<<<=====
finished output detect: 0
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

waiting for X server to begin accepting connections 
giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```
PAL-G, PAL or NTSC lead to the same error message.

If I take the vesa driver I get the nearly the same error message:
```

Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux debian 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May 22 23:54:57 2008
(==) Using config file: "/etc/X11/xorg.conf"

(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
NTSC PAL NTSC-J 
finished output detect: 0
(II) Module "ddc" already built-in
=====>>>>> (EE) VESA(1): No matching modes <<<<<=====
=====>>>>> (EE) Screen(s) found, but none have a usable configuration. <<<<<=====

Fatal server error:
no screens found

waiting for X server to begin accepting connections 
giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```
Do anybody have an idea to make it work through xorg.conf?

---

### Post by gekkoo on 2008-05-24
I was able to solve my problem through the german ubuntu forum. If anybody is/was interested in the solution:

I've reverted all the changes on my xorg.conf and used xrandr. With xrandr you can activate the S-Video output, set the tv standard etc. It has worked for me, so now I'm able to show my Display on my tv.

Here is a little script which I've written to turn on/off the tv screen
```

#!/bin/bash

# Useful if mplayer doesnt show anything on one of the displays
#xvattr -a XV_CRTC -v 1
#xvattr -a XV_CRTC -v 0

if [ "$1" = "on" ]
then
	MODES=$(xrandr -q | tail -n 1 | awk '{print $1}')
	# If no modes are set, add some
	if [ "$MODES" = "S-video" ]
	then
		echo "Adding 800x600 mode to S-video..."
		xrandr --addmode S-video 800x600

		# Could be useful...someday
		# xrandr --output S-video --auto

		echo "Setting TV standard to pal..."
		xrandr --output S-video --set tv_standard pal
	fi

	echo "Enabling 800x600 mode..."
	xrandr --output S-video --mode 800x600

	echo "Putting S-video to the right part of the screen..."
	xrandr --output S-video --right-of LVDS

elif [ "$1" = "off" ]
then
	echo "Disabling S-video..."
	xrandr --output S-video --off

else
	echo "Usage: tvout {on|off}"
fi                    

```
LVDS is the LCD Display of my laptop. If you do not want a stretched desktop delete > xrandr --output S-video --right-of LVDS from the script.
If you want to use a stretched desktop leave the script as it is, but you will need to add one line to your xorg.conf. Look up your Screen section and add the **Virtual** line, like in the example below.
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
		Virtual          1824 768
	EndSubSection
EndSection

```
1824 768 is the maximum screen size if I activtate my tv. (1024x768 + 800x600 = 1824x768, 768 because you take the biggest value of the resolutions)

---

