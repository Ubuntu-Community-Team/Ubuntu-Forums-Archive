---
title: "Graphics not working properly."
date: 2008-07-09
forum: Multimedia Software
---

### Post by sunithbalan on 2008-07-09
I have installed ubuntu hardy on my IBM t41 thinkpad.
The VGA  is 
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

I had also setup compiz. All things were fine and working smoothly.

But suddenly now the graphics has become very slow. 
I tried a lot of things by changing the xorg.conf, reinstall xserver etc etc

I guess the problem happened after some update of softwares.


Xorg.conf 
------------------------------
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
Identifier "Configured Video Device"
Boardname "ATI Radeon"
Busid "PCI:1:0:0"
Driver "radeon"
Screen 0
Vendorname "ATI"
Option "MergedFB" "off"
Option "AccelMethod" "EXA"
Option "EXANoComposite" "false"
# Option "AGPFastWrite" "On"
Option "XAANoOffscreenPixmaps"
Option "FBTexPercent" "50"
Option "MigrationHeuristic" "greedy"
Option "DRI" "true"
Option "GARTSize" "256"
Option "RenderAccel" "true"
Option "AGPMode" "2"
Option "Colortiling" "On"
Option "AGPSize" "32"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Option "AIGLX" "true"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "enable"
EndSection

------------------------------------------------------


Now compiz is not working, and all the windows are slow.
The screen resolution is not coming up. Totally frustrated.

Help me guys..


Sunith

---

### Post by unoodles on 2008-07-09
You could try "sudo dpkg-reconfigure -phigh xserver-xorg"

or try booting into recovery mode and there will be an option to "Fix X-Server" (if you are using Hardy)

---

### Post by sunithbalan on 2008-07-09
when i do 
sudo dpkg-reconfigure -phigh xserver-xorg

the device section in xorg.conf will be set to

Section "Device"
        Identifier      "Configured Video Device"
EndSection

---

### Post by sunithbalan on 2008-07-10
i managed to fix the problem.
I just removed the xserver-xorg and installed it again.

sunith

---

