---
title: "Screen Resolution Woes!!"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by Feck on 2007-06-03
Hey folks!
     I'm now running Ubuntu Feisty on a HP Pavilion dv9330 laptop, with the Nvidia GeForce Go 7600 graphics card. I've installed Beryl just fine after a bit of xorg.conf tweaking. Now, one major problem remains:

My laptop monitor and graphics card are able to support 1440x900 resolution, as that is what is runs while in Vista Ultimate (on the other partition). However, when I select 1440x900 resolution in Ubuntu, my screen glitches out and I have to restart X to get the screen resolution to reset itself and to be able to use anything at all. It should be noted that everything seems to glitch out to the bottom 1/4 of my screen, and I literally can't do anything. I used Envy to update/install the latest drivers (as far as I know, anyway), and still it won't work correctly.

Anyone know of an inherent solution to this problem? 'Cause 1280x800 seems to appear a bit fuzzy and large on my screen, since it's a 17" widescreen.

Cheers,
Feck

---

### Post by Pragmatist on 2007-06-04
Please attach your **/etc/X11/xorg.conf**

---

### Post by Feck on 2007-06-06
Sorry for the delay! Had some last minute work needing to be done in Windows. Here is my xorg.conf file:

```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"nVidia Corporation G70 [GeForce Go 7600]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce Go 7600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Anyone see any inherent issues?

---

### Post by Pragmatist on 2007-06-06
According to this page:
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9297ea?highlight=%28pavilion%29](https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9297ea?highlight=%28pavilion%29)

Looks like you either lookup the fix listed on that page, if your using 386 processor, or you switch from the "nv" driver to the "nvidia-glx" driver.

---

### Post by Feck on 2007-06-06
Tried the nvidia-glx thing, wouldn't load x at all. same with changing it to just nvidia. no X. so as it stands, I'm stuck with nv, even though I've used Envy to install the latest nvidia drivers...this is getting weird. Is this because I'm on an x64 system that the nvidia isn't working right, then? Or should that even matter?

---

