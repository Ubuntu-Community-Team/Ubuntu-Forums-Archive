---
title: "Nvidia driver ruins resolution"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by sargonious on 2008-02-23
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:0:13:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

That is my xorg.config file. I cannot figure out why it's not allowing me to display on my monitor's native resolution of 1280x1024, instead it's on 1280x960 and I cannot even change the resolution. It does nothing when I attempt to select the other ones. It asks me to keep the resolution or revert to the old one in which on whichever I decide nothing changes not even a monitor re sync. Can someone help me on how to fix this. I did run the command "sudo dpkg-reconfigure -phigh xserver-xorg" and it worked on VESA but I need my graphics acceleration with the restricted drivers.  The monitor is a Princeton VL173.

---

### Post by Sam Lars on 2008-02-23
Does 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
help?

---

### Post by Yellow Pasque on 2008-02-23
I'll assume you're shooting for 1280x1024 @ 60Hz. Generate a modeline with this command:
```
cvt -v 1280 1024 60.0Hz
```
Paste the result into the Monitor section (after the Vertrefresh line)

In your screen section, add this block of code after the "defaultdepth 24" line
```
SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"
	EndSubSection
```
Save. Reboot.

---

