---
title: "Help me get rid of underscan (get more overscan)"
date: 2008-08-14
forum: Multimedia Software
---

### Post by Redsandro on 2008-08-14
Hi,

I am having trouble getting my TV-out through S-VHS from a nVidia-legacy geForce MX card to fill the entire television screen.

My xorg.conf is manually created by taking snippets off this forum because anything automatically generated simply wouldn't work. I am not really getting the 8 extra numbers that go into the ModeLine I read in some topics. It doesn't look like the ones I got at all. Also they are often about HDTV. I'm just using an oldschool TV with a legacy card.

Here's the relevant part of my xorg.conf:[SIZE="1"]```
#
# Monitors
#

Section "Monitor"
    Identifier     "Monitor_VGA"
    VendorName     "Philips"
    ModelName      "Philips 107B(17inch/CM6800)"
    HorizSync       30.0 - 69.0
    VertRefresh     50.0 - 130.0
EndSection

Section "Monitor"
    Identifier     "TV_SVIDEO"
    VendorName     "Blaupunkt"
    ModelName      "Nageaapt van Grundig TV"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

#
# Video kaarten
#

Section "Device"
	Identifier	"Video_MX200"
	Driver		"nvidia"
	VendorName	"nVidia Corp"
	BoardName	"nVidia Geforce2 MX200 (legacy)"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	Option		"AddARGBVisuals" "True"
	Screen		0 # deprecated?
EndSection

#
# Screens - verbindingen
#

Section "Screen"
# Monitor met TV Clone
	Identifier     "Screen_Both"
	Device         "Video_MX200"
	Monitor        "Monitor_VGA"
	DefaultDepth    24

	Option		"TwinView" "1"
	Option		"metamodes" "CRT: 1024x768 +0+0, TV: 800x600@1024x768; CRT: 800x600 +0+0, TV: 800x600 +0+0; CRT: 640x480 +0+0, TV: 640x480 +0+0; CRT: 1280x1024 +0+0, TV: NULL; CRT: 1152x864 +0+0, TV: NULL;"
	Option		"TVOutFormat" "SVIDEO"  # Or "COMPOSITE"
	Option		"TVStandard" "PAL-B"
	Option		"RenderAccel" "On"
	Option		"HWcursor" "On"
	Option		"DamageEvents" "True"
	Option		"AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

#
# Server Layouts - Resoluties beschikbaar voor Xserver
#

Section "ServerLayout"
    Identifier     "PrimaryLayout"
    Screen      0  "Screen_Both" 0 0
    InputDevice    "myKeyboard" "CoreKeyboard"
    InputDevice    "myMouse" "CorePointer"
EndSection

```[/SIZE]

Monitor: Good (enough):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=81524&stc=1&d=1218708990[/IMG]

TV: Too much underscan?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=81523&stc=1&d=1218708990[/IMG]

[SIZE="1"]The guy in the picture is actor Carlos Bernard. Don't worry, he'll be fine.[/SIZE]

---

### Post by Redsandro on 2008-08-15
Just to be more specific, MX cards are GeForce2's, so they don't support the TVOverScan option mentioned in the nvidia-glx-legacy-readme. They are for GeForce 4 and up.

---

