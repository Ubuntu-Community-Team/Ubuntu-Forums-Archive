---
title: "NVIDIA xorg LCD(DVI)+CRT 7800GTX"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by illuzian on 2006-09-22
Hey all,

I feel like a total newb here but I'm making the move from Windows to Linux as my desktop however I do have a debian server running and a CC gateway so I am not a complete newb.

My problem is one that I can't get my head around, and I couldn't find my answer after searching both the forums and my great friend google/google linux.

Apologies if this has been answered before.. if so and you know where point me in the right direction.

-----Question-----
I have a a NVIDIA 7800 GTX with two video outs and I want to run TwinView

The monitors connecting are:
-CRT Likom 17" L706*** (analogue out)
-LCD Viewsonic 17" VP171b (DVI Out)

After installing the nvidia binary driver the DVI monitor is either configured as Generic Monitor or completely ignored and the LKM is configured only(my deb machine connecting to the 1st analogue in of the monitor recognizes this monitor as the Viewsonic so I assume the problem is with the DVI?(this monitor allows 3 simultaneous connections 1 DVI 2 Analogue... switchable like monitor switching on a KVM).

I have tried manually editing the xorg.conf but it either doesn't load up or when X starts it just hard locks the system... Or only the CRT shows and the monitor doesnt detect a signal and switched to one of the other monitor cables connected to it(the analogues).

At this very moment I have no xorg.conf file to put here but I was wandering if anyone had any suggestions on the xorg.conf adjustments that need to be made to have:

TwinView xinerama
Viewsonic DVI Right Monitor
LKM Right Monitor

It would be ideal if anyone who had a similar config with the same LCD and a CRT could post their latter half of the xorg.conf file so I can test/adapt it.

I'm currently on my win machine now and will be reinstalling Ubuntu soon and removing xorg/gdm from starting in runlevel 3(don't know the ubuntu runlevel config but I assume its the same as Debians) so I can boot to RL3 for editing.(reinstalling as x86 as opposed to x64.. don't ask)

If you guys required xorg logs(I've checked them and they don't report anything that odd) or an example of my to be xorg config file I can certainly post it once I'm up.

Anyways sorry for this long winded post and I hope I don't come across too tool-ish... thanks in advanced.

[-]
Side note.. In all relevance the extra analogue ports on the monitor aren't relevant apart from the auto detection of the monitor while connected to an analogue connector.
[-]

---

### Post by tseliot on 2006-09-22
Try this guide:
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by illuzian on 2006-09-23
None of the material provided was at all conclusive but I finally have my rig setup took me about 2 hours to get the ideal setup but in regards to video the following is the video section of my xorg.conf for:
DVI - LCD
Analogue - CRT
Twinview
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "UseDisplayDevice" "DFP, CRT"
	Option "TwinView" "True" 
	Option "TwinViewOrientation" "RightOf" 
	Option "UseEdidFreqs" "False" 
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
#Option "ConnectedMonitor" "dfp, crt"
	Option "SecondMonitorHorizSync" "31-82"
	Option "SecondMonitorVertRefresh" "56-76"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
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
EndSection

```

I'm not a perfectionist so Ignore the ATI crap.. it works fine.

I'm sure its not perfect either but for now im :) so for anyone wanting instant TwinView satisfaction with a similar setup this should work....

---

