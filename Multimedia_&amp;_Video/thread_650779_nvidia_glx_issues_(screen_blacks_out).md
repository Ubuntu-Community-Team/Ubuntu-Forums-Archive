---
title: "nvidia glx issues (screen blacks out)"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by ishkabob on 2007-12-26
Hi all,

I just got myself a new 22 inch Samsung Syncmaster 220WM monitor and am having some issues with it.  I decided that as long as I was messing with my xorg.conf that I would update my video drivers.  I went to the nvidia website and downloaded the latest drivers and installed.  I then ran

```
sudo dpkg-reconfigure xserver-xorg
```

being careful to enter the resolutions and horizontal and vertical refresh rates suggested by Samsung.

Everything looks fine, but whenever I run anything that uses glx (glxgears, a video game etc.), it seems to run ok but the screen will go black every 5 seconds or so (sometimes more erradically).

I tried removing the drivers and just using the nvidia-glx-new package from the repositories ( I have a GeForce 8400 GS ), but the exact same thing happens.  I know these drivers in the repos are 1 version behind what's on the Nvidia website too.  I'm assuming I messed something up in the xorg.conf when i reconfigured.  I've attached my xorg.conf below. Any Ideas?

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8400 GS]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8400 GS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1440x900" "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

---

### Post by ishkabob on 2007-12-27
bump

---

### Post by adelodder on 2007-12-27
I suggest you install the drivers using [Envy.]("http://albertomilone.com/nvidia_scripts1.html")  It should configure your xorg.conf correctly.

---

### Post by ishkabob on 2007-12-27
Ok, I'll give that a try.  Thank you!

---

### Post by ishkabob on 2008-01-02
Thanks for the advice on using Envy, so much easier!  It turns out that when I use a VGA cable, as opposed to a DVI cable, to connect my monitor, I have no problems.  It sounds strange to me though that GLX would cause a problem with DVI output.  Has anyone had a similar experience?

---

