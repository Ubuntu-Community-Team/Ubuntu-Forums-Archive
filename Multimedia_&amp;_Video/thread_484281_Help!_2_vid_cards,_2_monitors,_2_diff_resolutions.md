---
title: "Help! 2 vid cards, 2 monitors, 2 diff resolutions"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by random_user on 2007-06-25
I need help! I've tried and tried to get this thing working.  I want to do 2 diff cards (intel onboard, ati radeon 9200 PCI) with 2 diff. monitors at 2 diff. resolutions.  What's happening is I get output from my ATI just fine, but I get no output from my intel.  I was pretty sure I had this set up properly.  Here are relevant sections from my xorg.conf:

## FOR THE ATI DRIVER ################################################
Section "Device"
	Identifier	"ati"
	Driver		"vesa"
	BusID		"PCI:1:1:0"
	Screen		0
EndSection

Section "Monitor"
	Identifier	"BenQ T705"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ati"
	Monitor		"BenQ T705"
	DefaultDepth	24
   #  ... (other display sub-sections)
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

##################################################################

## FOR THE INTEL INTEGRATED ######################################

Section "Device"
	Identifier	"intel"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Dell 1505FP"
	VendorName 	"Dell"
	ModelName	"1505FP"
	Option		"DPMS"
	HorizSync	30-61
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"intel"
	Monitor		"Dell 1505FP"
	DefaultDepth	24
       # ... (other display sub-sections)
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

#################################################################

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen0" 
	Screen 1	"Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


Here is a line from my Xorg.0.log that seems to make note of the intel integrated not working.

... stuff ...
(WW) I810: No matching Device section for instance (BusID PCI:0:2:0) found
(--) Chipset 865G found
... more stuff ...
(EE) Screen 1 deleted because of no matching config section.
(II) UnloadModule: "i810"

And in case someone wants to see lspci:
...
00:02.0 Display controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
...
01:01.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:01.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
...

And I think that's it for the relevant information :) Hopefully someone can help! Thanks!

---

