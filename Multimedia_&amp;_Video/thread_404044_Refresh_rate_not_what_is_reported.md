---
title: "Refresh rate not what is reported"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by kpm on 2007-04-07
Hi, 

I have two laptops hooked up via a KVM to an old Visual Sensations KDS monitor.
One of the laptops  has a broken LCD, the others works, but I shut it off because getting xorg.conf to work properly for dual monitor set up turned out to be as much fun as a sharp stick in the eye! But thats another story...

My current pressing problem is that all though Ubuntu' s "Screen Resolution Preferences" dialogue displays an 86Hz refresh rate, both my eyes and the On Screen Control of KDS monitor say other wise.  The OSD claims the following:
"User Mode Hf: 63.9kHz Vf: 60Hz"

Here is the video and monitor part of my xorg.conf file, all pretty generic, I added the 'HorizSync 30-95' and 'VertRefresh 50-120', but it didn't seem to help... 


[code]Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Visual Sensa"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Visual Sensa"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection[\code]

If any one has any ideas as to how I can bump the refresh rate of this old crt up to the 85 Hz level, you may help prevent this 60 Hz flickering from inducing a seizure!

Thanks,
kpm

---

### Post by kpm on 2007-04-08
Ok, I solved the vertical refresh rate problem by switching the graphics driver section of the xorg.conf file from this:
[HTML]Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection [/HTML]
to this:
[HTML]Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection[/HTML]
I would like to completely kill the screen on the laptop since it is broken, and hitting the function key and the monitor selection key, I think is what I did before to shut it off on the laptop, but it is remaining on now, which I beleive is causing a new problem... The CRT should be able to run at 1280x1024 but it is showing only a maximum of 1024x768 resolution.
Anyone know how I can get 1280x1024 res back and keep the high refresh rates as well?

Thanks

---

