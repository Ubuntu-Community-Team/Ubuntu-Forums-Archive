---
title: "1600x1200 w/60 Hz vert refresh - can't make it work"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by picker77 on 2007-02-01
Searched all the threads I could find, tried the fixes, ran xorg reconfig, etc with no success. Running the latest Edgy w/updates using a brand new Dell 2007FP 1600x1200 capable LCD and Intel graphics. This monitor requires a 60 Hz vertical refresh for 1600x1200 mode, everything else runs at 75 Hz. Everything works great in XP, but when I boot up Ubuntu Edgy I get a monitor error message telling me it can't display this mode, and to reset my vert refresh to 60, at which time I have to fall back to 1280x1024 @ 75 Hz using CTRL-ALT+, which works just fine. Once up and running in 1280x1024/75, SYSTEM/PREFERENCES/SCREEN RESOLUTION gives me five choices: 640x480 through  1280x1024 (all at 75 Hz), plus 1600x1200 @ 65 (not 60!) Hz. There is no other choice in the refresh rate drop-down menu other than 65 when I select 1600x1200. I haven't a clue where this "65" number is coming from. The monitor, of course, won't display at 65 Hz, and I've been unable to figure out how to get that 65 Hz changed to the 60 Hz required by the monitor.. Relevant sections of my current Xorg.conf are:

Section "Monitor"
	Identifier	"DELL 2007FP"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"DELL 2007FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Telling it to use 1600x1200 @ 60 Hz during the Xorg reconfig simply doesn't seem to "take". After booting up, my ONLY 1600x1200 choice for vert refresh rate is again 65 Hz. I hope I haven't missed anything obvious searching the forums, but any help would be greatly appreciated. Is there a way to force 60 Hz vs 65 Hz when using 1600x1200? Where is the "65" coming from - my vbios? I hate to waste the hi-res capability of this great new monitor. Thanks in advance for the help!

---

### Post by p!=f on 2007-02-01
Try this (works on my DELL 1907FP for its optimal 1280x1024@60), success not guaranteed though. :)
> 
Section "Monitor"
 Identifier "DELL 2007FP"
 Option "DPMS"
 HorizSync 30-83
 VertRefresh **60-60**
 **Modeline "1600x1200" 160.96 1600 1704 1880 2160 1200 1201 1204 1242 -HSync +Vsync** *#try to comment if not working*
 EndSection
 
 Section "Screen"
 Identifier "Default Screen"
 Device "Intel Corporation 82865G Integrated Graphics Controller"
 Monitor "DELL 2007FP"
 **DefaultDepth 16** *#be sure your card can handle 24 or lower to 16*
 SubSection "Display"
 Depth 1
 Modes "1600x1200@**60**" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
 Depth 4
 Modes "1600x1200@**60**" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
 Depth 8
 Modes "1600x1200@**60**" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
 Depth 15
 Modes "1600x1200@**60**" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
 Depth 16
 Modes "1600x1200@**60**" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
 Depth 24
 Modes "1600x1200@**60**" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
 EndSubSection
 EndSection


---

### Post by picker77 on 2007-02-01
Eureka!!! Worked like a Swiss watch!  Thanks...

---

### Post by picker77 on 2007-02-01
Just for a test drill, once I had it working I went back in and changed the 60-60 vert refresh back to the original 56-76 value, and it still worked, so it looks like it's the **Modeline** that's important here.
Thanks again.

---

