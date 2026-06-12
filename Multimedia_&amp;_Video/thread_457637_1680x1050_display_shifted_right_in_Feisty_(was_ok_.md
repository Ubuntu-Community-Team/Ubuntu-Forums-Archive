---
title: "1680x1050 display shifted right in Feisty (was ok in Edgy)"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by chmod000 on 2007-05-28
I know this topic has been beaten to death but I'm having a problem that I haven't been able to fix for several weeks.  I originally had everything working perfectly fine in Edgy but after I upgraded to Feisty the problem has resurfaced and using my previous xorg.conf file isn't fixing things.  

1. The screen is shifted about 40mm to the right.
2.  I dual-boot unfortunately so I can't just reset my monitor's settings.
3. I can run xvidtune, click Left four times, click apply, and get everything looking fine.  I then click on 'Show' and it tells me that my current settings are exactly what I have as my Modeline in my xorg.conf file.  After a restart, the screen is shifted over again.



*Is there some command I need to execute after I update the xorg.conf file in order to really set the update?

___________________________________
Section "Device"
	Identifier	"NVIDIA GeForce"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
	Modeline "1680x1050"   146.25   1680 1800 1976 2240   1050 1053 1059 1089 +hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
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

______________________________________________
 
Any help is greatly appreciated.

---

