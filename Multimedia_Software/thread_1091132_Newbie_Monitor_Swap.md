---
title: "Newbie Monitor Swap"
date: 2009-03-09
forum: Multimedia Software
---

### Post by slightlystoopid on 2009-03-09
So I'm merely trying to go from a KDS XF-7bk crt to an LG 566LM lcd. Of course, my world has collapsed from 1024x768 to 640x480. I know the frequency settings are now invalid, but nvidia-settings gives me no options to change my display, and without altering the frequency settings, preferences - resolution doesn't give me any options with the new monitor. I know I've used some other configuration utility in the past, but it's been over a year and I can't remember or find the same/currently useful information about it. I've also manually tweaked an xorg.conf file at some point, but I can't seem to find whatever xorg.conf is being read by the system. It's certainly none of the ones stored in /etc/X11/. Not one contains a single line of current videocard, monitor, or mouse specifications, but those are the only ones 'locate xorg' finds. I didn't delete anything, the configuration exists somewhere, everything still looks beautiful on the crt. 'dpkg-reconfigure xserver-xorg' only asks keyboard questions. 'Xorg -configure' causes the screen to go blank for about 30 seconds save for a couple lines about the firewall and network going down, then the system decides to reboot without change. where is the configuration file and what utility can I use to edit it?

---

### Post by slightlystoopid on 2009-03-09
I am completely and thoroughly confuddled and flabbergasted. 'grep -i -c HorizSync' returns no configuration files. .nvidia-settings-rc contains no sync information. Somewhere on planet ubuntu there's HorizSync info and Screen0 with Mode info. I'd love to know where it is and why grep can't find it. I should probably add that I don't wish to completely re-write the file, only append info for the new monitor.

if anyone's interested, this is my xorg.conf file:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection
```

---

### Post by slightlystoopid on 2009-03-09
Ok, I wrote my own xorg.conf. I'll throw it in /etc/X11/ as soon as I get a dvi to vga adapter and see what happens.

```

Section "Module"
#	Load	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"glx"
#	Load	"record"
#	Load	"xtrap"
	Load	"freetype"
EndSection

Section "Device"
	Identifier	"Card0"
	Driver		"nvidia"
	VendorName	"nVidia Corporation"
	BoardName	"nVidia GeForce FX 5200"
	BusID		"PCI:1:0:0"
#	Screen		0
	Option	"NvAGP"		"1"
	Option	"Coolbits"	"1"
	Option	"RenderAccel"	"True"
	Option	"NoLogo"	"True"
	Option	"TwinView"	"True"
	Option	"TwinViewOrientation"	"RightOf"
	Option	"UseEdidFreqs"	"True"
#	Option	"NoTwinViewXineramaInfo"	"True"
EndSection

#Section "Device"
#	Identifier	"Card1"
#	VendorName	"nVidia Corporation"
#	BoardName	"nVidia GeForce FX 5200"
#	Driver		"nvidia"
#	BusID		"PCI:1:0:0"
#	Screen		1
#	Option	"NvAGP"		"1"
#	Option	"Coolbits"	"1"
#	Option	"RenderAccel"	"True"
#	Option	"NoLogo"	"True"
#EndSection

Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"LG"
	ModelName	"566LM"
	HorizSync	30.0 - 63.0
	VertRefresh	50.0 - 75.0
	Option	"DPMS"	"true"
EndSection

#Section "Monitor"
#	Identifier	"Monitor1"
#	VendorName	"KDS"
#	ModelName	"XF-7bk"
#	HorizSync	30.0 - 70.0
#	VertRefresh	50.0 - 160.0
#	Option	"DPMS"	"true"
#EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Card0"
	Monitor		"Monitor0"
	DefaultDepth	24
	Option	"MetaModes"	"1024x768,1024x768; 1024x768, NULL; NULL, 1024x768"
	Option	"SecondMonitorHorizSync"	"30.0 - 70.0"
	Option	"SecondMonitorVertRefresh"	"50.0 - 160.0"
	SubSection "Display"
		Depth	24
		Modes	"1024x768"
		Viewport 0 0
	EndSubSection
EndSection

#Section "Screen"
#	Identifier	"Screen1"
#	Device		"Card1"
#	Monitor		"Monitor1"
#	DefaultDepth	24
#	SubSection "Display"
#		Depth	1
#		Modes	"1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth	4
#		Modes	"1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth	8
#	       	Modes	"1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth	15
#		Modes	"1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth	16
#		Modes	"1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth	24
#		Modes	"1024x768" "800x600" "640x480"
#	EndSubSection
#EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen0" 0 0
#	Screen 1	"Screen1" RightOf "Screen0"

#	Option	"Xinerama"	"true"
	Option	"clone"		"false"
EndSection
```

---

### Post by norwoods on 2009-03-10
run sudo nvidia-xconfig to generate a new /etc/X11/xorg.conf

---

### Post by slightlystoopid on 2009-03-10
yeah, thanks, but it just generates what I pasted in my second post. The latter xorg.conf works great though with the twinview lines commented out for now.

---

### Post by norwoods on 2009-03-10
you get a command line by starting Applications--Accessories--Terminal
run gksu nvidia-settings

to get twinview, click Configure...
click the TwinView radio button

---

### Post by slightlystoopid on 2009-03-10
I suppose I forgot to mention I tried everything by switching to a different virtual terminal then running 'sudo /etc/init.d/gdm stop' first. then starting it back up. only issue now is finding correct modeline values as according to xorg.0.log, the edid values it detects are invalid.

---

### Post by slightlystoopid on 2009-03-10
As a result of the Edid not being readable, I added```
Option "UseEDID" "False"
```
Using the reciprocal of the dot pitch multiplied by millimeters in an inch leads me to add the line```
Option "DPI" "85 x 85"
```
However, I'm anticipating this being an issue in a dual monitor setup. How is that going to work? Can there be separate DPI's set for each monitor?

---

### Post by norwoods on 2009-03-10
i increase the DPI for both monitors but the same value.  it appears that you may be able to achieve the effect with scaling; set one of the monitors to something other than its real resolution and scale it to fit..

---

