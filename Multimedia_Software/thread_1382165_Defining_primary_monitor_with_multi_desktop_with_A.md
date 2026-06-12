---
title: "Defining primary monitor with multi desktop with ATI catalyst"
date: 2010-01-15
forum: Multimedia Software
---

### Post by marchost on 2010-01-15
Hi all, i'm currently trying to find a way to define which display will be the primary.

I have a 22inch on the left of a 24 inches.

Currently, the screen #1 is the 22 inches, on which the login screen appear.

What I want is the 24 inches to be the primary display. Unfortunately, there is no such option in the catalyst control center...

Setup : 9.10 AMD64, using catalyst drivers from ATI (latest.

Here is a copy paste of my xorg.conf :

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "amdcccle-Screen[7]-1" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP5"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1680 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP5" "0-DFP5"
	BusID       "PCI:7:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "amdcccle-Device[7]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "0-CRT2"
	Option	    "Monitor-DFP5" "0-DFP5"
	BusID       "PCI:7:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3600 3600
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[7]-1"
	Device     "amdcccle-Device[7]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3600 3600
		Depth     24
	EndSubSection
EndSection

---

### Post by evenstranger on 2010-02-16
Having similar problems want to specify which of the two monitors is the primary with ati multi monitor setup. Did you make any progress on this ?

---

### Post by bobonthenet on 2010-05-28
Any solution for this yet?  I am also having the same problem.  I am afraid to modify my xorg.conf because every time I so much as look at it my video settings get totally messed up!

---

### Post by volgatha on 2011-02-23
bump. I am having the same problem.

---

### Post by bobonthenet on 2011-02-23
I never resolved it myself.  I just gave up.

---

### Post by tanzoniteblack on 2011-04-07
as discussed in [http://ubuntuforums.org/showthread.php?t=1309247]("http://ubuntuforums.org/showthread.php?t=1309247"):

The command xrandr allows for the switching of primary monitor

To change primary monitor to CRT1:
```
xrandr --output CRT1 --primary --auto --pos 0x0 --output LVDS --auto --left-of CRT1
```

Obviously switch CRT1 with the name for the monitor you want to be default, LVDS with the one you want to be secondary, and --left-of with the location you'd like

to switch back to single monitor mode:
```
xrandr --output CRT1 --off --output LVDS --auto
```

You can map these commands to keyboard short cuts for easier use.  Every time I do the switch though, the red screen identifiers come up and I have to turn those off by opening catylist and toggling show identifiers...not sure how to fix that yet.

---

### Post by gewone on 2011-10-13
Nice going tanzoniteblack!

The "xrandr --output CRT1 --primary --auto --pos 0x0 --output LVDS --auto --left-of CRT1" is instantly fixing my setup so that my ancient VGA-attached desk monitor gets to be primary, and my flat-telly goes to be secondary. However, I need to push this command every time I want things to happen. Is there any way to invoke this on startup? Or even better, something to write into xorg.conf to have it act right?

---

### Post by tanzoniteblack on 2011-10-13
If you save this command in a text file as something .sh (e.g. multimonitors.sh), and include the line #! /bin/bash at the top , set the file permissions so the file can be executed, you can add it to your start up programs.

example of a multimonitors.sh:

#! /bin/bash
xrandr --output VGA1 --primary

however, I warn you, they changed how Unity's side bar works in 11.10. The placement of the unity bar is no longer decided based on which monitor is primary, but has been switched so that it is always on the left most edge of the "screen" (the conglomeration of the two monitors).

In my home set up, I have my laptop on the left, and my external monitor on the right.  If I want to have the unity side bar on my external monitor, I have to tell Ubuntu in the display menu that my laptop is to the right of my external, and to move to the monitor on the left, I have to go across the right screen edge of my right monitor.  It's a little strange....

---

### Post by gewone on 2011-10-14
Big thanks to you tanzoniteblack!

I really like where we're going with this.
I haven't installed 11.10 just yet.
Give me a day or so, and I'll report back!

The "changes" you described may (or may not be) in my favor.

---

### Post by tanzoniteblack on 2011-10-14
To be honest, as bizarre as it is to go off the right edge of the screen to get to the left monitor, I actually like it more than the previous set up.  There were always a few bizarre hiccups before due to having cross over the unity launcher to get to the other screen, especially when dragging windows and files. Forcing the Unity launcher to be the leftmost item was a very simple fix to some of these bizarre behavior issues.

---

### Post by tamashumi on 2011-10-15
Guys, check this out, [a solution]("http://ubuntuforums.org/showpost.php?p=11346991&postcount=16") which worked for me with ATI.

@gewone
Don't go for 11.10 if you use proprietary driver and Unity or Compiz. Catalyst 11.9 doesn't work with 11.10 and will break 3D. However default driver which comes with Ubuntu worked fine.

---

