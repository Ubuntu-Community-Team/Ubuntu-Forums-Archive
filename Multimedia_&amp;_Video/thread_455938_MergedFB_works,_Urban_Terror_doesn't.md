---
title: "MergedFB works, Urban Terror doesn't"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by WarLocke on 2007-05-27
Hello,

I just set up my ATI Radeon 9660 Pro (Dual Head) with 2 monitors using MergedFB.  My setup is this: My main monitor (LCD) is on the right, and I have a spare CRT on the left.  Everything seems to be up to par until I start Urban Terror.  It cuts off half of the screen to the right of my main monitor, and the rest is just black on that screen.  Any ideas on how to fix it?  This is my /etc/X11/xorg.conf

```

Section "Device"
	Identifier	"ATI Radeon 9660"
	Driver		"ati"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"
	Option 		"MergedFB" "true" #Enable MergedFB function
	Option 		"MonitorLayout" "CRT, CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  	Option 		"CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  	Option 		"CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  	Option 		"OverlayOnCRTC2" "true"
  	Option 		"CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  	Option 		"MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
	Option 		"MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Tyris"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9660"
	Monitor		"Tyris"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
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
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Thanks in advance for any help! :D

---

### Post by WarLocke on 2007-05-27
bump....

Does anyone have an idea?  Been googling but I came up empty :(

---

### Post by WarLocke on 2007-05-31
BUMP!!!

Anyone?

---

