---
title: "AL2216W Squished Screen"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by chadmounteny on 2007-10-28
Hello;

I'm having troubles running an Acer AL2216W with Ubuntu 7,10 Desktop, After doing what I think is the proper setup in the xorg.conf file (or after letting xorg or the 'Screens and Graphics' widget  try to do the configuration) I end up with the screen showing the proper resolution of 1680X1050 (reported as so in the info box contained in the OSD of the monitor) but with the wrong Aspect Ratio. The screen is formatted if as it was a 4:3 LCD so that the information on screen is severely squished along the horizontal axis.

I have tried connecting it to both of the video cards I have at my disposal and the results are the same.

The cards are (as detected, but also match the physical markings on the cards);
"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
"ATI Technologies Inc RV280 [Radeon 9200]"


1680 X 1050 is the native resolution of the monitor and it does work properly in Windows.

Both cards only have VGA out.

What follows are relevant extracts from xorg.conf files.
(These settings are what were picked automatically by 'dpkg-reconfigure xserver-xorg'
although I explored using settings from various other postings that I could find that seemed related, none helped.)

With the ATI Radeon Enabled;
```

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL2216W"
	Option		"DPMS"
	HorizSync	47-84
	VertRefresh	56-76

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200]"
	Monitor		"Acer AL2216W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050"
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

With the NVIDIA enabled;
```

Section "Device"
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:0:6:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL2216W"
	Option		"DPMS"
	HorizSync	47-84
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Acer AL2216W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050"
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

Thanks!
Chad M

---

