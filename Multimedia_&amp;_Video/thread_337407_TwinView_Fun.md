---
title: "TwinView Fun"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by Icemanyurt on 2007-01-12
I am getting the TV to flash from static to a non-image back to static on boot, here is the relevant parts of my xorg.conf...any help would be great...
I am going from Composite Out to an RF Modulator to a TV
> Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:5:0"
	Option		"NvAGP" "2"
	Option		"RenderAccel" "0"
	Option		"CursorShadow" "0"
	Option		"Connected Monitor" "crt, tv"
	Option		"NoPowerConnectorCheck"
	Option		"TwinView" "1"
	Option		"MetaModes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
	Option		"SecondMonitorHorizSync" "28-51"
	Option		"SecondMonitorVertRefresh" "43-60"
	EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"TwinView Configuration"
	Screen 0	"Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option 		"Xinerama" "Off"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection



---

### Post by Icemanyurt on 2007-01-13
bump

---

### Post by kebes on 2007-01-13
It would help if you described in a little more detail what your hardware setup is, and what xorg changes you've already made.

Your xorg.conf looks like it's configured to run two identical LCDs that have native resolution of "1280x1024". This is not your setup, I guess, since you mentioned that you're using a composite out to a TV.

Are you trying to output to a LCD and simultaneously to a TV? (And are they supposed to be mirrors of the same thing, or span to create 'one big desktop'?) ...or are you trying to solely output to a TV?

What video hardware are you using? Do you have two video cards? Do you have a video card with two outputs? Do you have a separate TV-out card?

Also, what changes have you made to xorg? You've enabled "twinview" which is normally used to span a desktop across two monitors. Is that what you want?



If you want TV-out, you need to define a monitor for your TV. It will look something like:
```
Section "Monitor"
    Identifier "NTSC Television"
    # D: 34.563 MHz, H: 37.244 kHz, V: 73.897 Hz
    HorizSync   30-68
    VertRefresh 50-120
    Mode "720x480"
         DotClock 34.564
         HTimings 720 752 840 928
         VTimings 480 484 488 504
         Flags "-Hsync" "-Vsync"
    EndMode
EndSection
```

(That's an NTSC, not PAL, television.) You similarly need a screen defined:
```
Section "Screen"
        Identifier "TV Screen"
        Device "nv card"
        Monitor "NTSC Television"
        DefaultDepth 24
        DefaultFbbpp 32

        Subsection "Display"
                   Depth 24
                   FbBpp 32
                   Modes "720x480"
        EndSubsection
EndSection
```

(Notice that we are defining the display mode as "720x480", which is a standard NTSC television screen.)

Finally you need your "ServerLayout" to use defined screen.

---

