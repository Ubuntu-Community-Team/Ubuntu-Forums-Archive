---
title: "Xinerama: X won't start"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by raharris on 2007-06-05
OK, I followd the Xinerama instructions and have come up with a number of problems.  All else aside it seems to boil down to X not starting because of the reference to "main screen" after "main monitor."   I've copied my xorg.conf below -- any help appreciated.
RAH


Section "Device"
	Identifier	"0 ATI Technologies Inc RV410 [Radeon X700 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		0
	Option 		"DDCMode" "True"
	Option 	"MonitorLayout" "primary monitor, secondary monitor" 
EndSection

Section "Device"
	Identifier	"1 ATI Technologies Inc RV410 [Radeon X700 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Screen		1
	Option 		"DDCMode" "True"
	Option 		"MonitorLayout" "primary monitor, secondary monitor" 	EndSection

Section "Monitor"
	Identifier	"DELL 1905FP"
	Option		"DPMS"
	HorizSync 	31.5-91.1
        VertRefresh 	60-100
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"0 ATI Technologies Inc RV410 [Radeon X700 (PCIE)]"
    	Monitor        "Main Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768"  
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 ATI Technologies Inc RV410 [Radeon X700 (PCIE)]"
    	Monitor        "Second Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" 
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" 
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" 
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" 
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" 
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
    	Screen      	0  "Main Screen"
    	Screen       	1  "Second Screen" RightOf "Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option 		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by raharris on 2007-06-05
never miiind -- I figured it out (eight edits of xorg.conf later . . . )

;)
RAH

---

