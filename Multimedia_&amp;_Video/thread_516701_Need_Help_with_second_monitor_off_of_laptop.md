---
title: "Need Help with second monitor off of laptop"
date: 2007-08-03
forum: Multimedia &amp; Video
---

### Post by jrmontg on 2007-08-03
I have a Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller on my laptop.  I have a Acer AL1717 monitor that I would like to span my display too.  I enabled everything that I thought I was suppose to but when I log out and log back in the second monitor does not come on.  PLEASE HELP 

This is my current xorg.conf
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
Section "Device"
        Identifier      "Intel 2 Monitor"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection
Section "Monitor"
        Identifier      "Acer AL1717"
        Option          "DPMS"
        HorizSync       30-82
        VertRefresh     56-76
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
Section "Screen"
Identifier "Screen2"
Device "Intel 2 Monitor"
Monitor "Acer AL1717"
DefaultDepth 24
Subsection "Display"
Depth 8
Modes "1600x1200@60" "1280x1024@60" "1152x864@60" "1024x768@60"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 16
Modes "1600x1200@60" "1280x1024@60" "1152x864@60" "1024x768@60"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 24
Modes "1600x1200@60" "1280x1024@60" "1152x864@60" "1024x768@60"
ViewPort 0 0
EndSubsection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0	"Default Screen"
	Screen 		1	"Screen2" RightOf "Default Screen"
	
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
Option "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by jrmontg on 2007-08-06
Anyone?  I am trying to figure this out before I install to my hard drive.  Thanks

---

### Post by optimarcus_prime on 2007-08-20
Just a thought:  does your external display have a list maximum/recommended resolution?  If so, it might be wise to simply set the only allowed resolution for that screen to that resolution.  For example, you have:
```

Section "Screen"
Identifier "Screen2"
Device "Intel 2 Monitor"
Monitor "Acer AL1717"
DefaultDepth 24
Subsection "Display"
Depth 8
Modes "1600x1200@60" "1280x1024@60" "1152x864@60" "1024x768@60"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 16
Modes "1600x1200@60" "1280x1024@60" "1152x864@60" "1024x768@60"
ViewPort 0 0
EndSubsection
Subsection "Display"
Depth 24
Modes "1600x1200@60" "1280x1024@60" "1152x864@60" "1024x768@60"
ViewPort 0 0
EndSubsection
EndSection
```

If the recommended resolution for the display is 1600x1200, you might want to change these subsections to:
```

Subsection "Display"
Depth 24
Modes "1600x1200"
ViewPort 0 0
EndSubsection
```

That's something that worked for me, anyways.

---

