---
title: "Totem-xine Detects Aspect Ratio Right, Displays Wrong"
date: 2008-08-15
forum: Multimedia Software
---

### Post by Themicles on 2008-08-15
Mplayer gets aspect ratios correct and draws them correct, but DVDnav support sucks.

Totem-gstreamer gets aspect ratios correct and draws them correct, but there's no ac3 passthrough.

Totem-xine has good DVDnav support, and working AC3 passthrough (after editing the totem xine config under .config/totem) but draws all video (dvds, video files, and even the visualizer for music!) wrong. It detects aspect ratios right, but draws them wrong. 16:9 on my 32" HDTV is nearly half the proper height. Setting the aspect ratio to 4:3 gets it close, but still doesn't draw it the full height. Estimate about 20 pixels off the top and bottom making it 40 pixels off on height if my guess is accurate.

Version: Ubuntu 8.04.1
uname -a: Linux beast-linux 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
Totem v: 2.22.1
xine-lib v: 1.1.11.1
Video: GeForce 7800 GS w/ default restricted driver
Display: Olevia LT32HV 32" HDTV connected via dual-link DVI
xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"GeForce 7800 GS"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
        Option   	"UseEdidDpi"	"false"
        Option   	"DPI"		"96 x 96"
EndSection

Section "Monitor"
	Identifier	"Olevia LT32HV"
	DisplaySize     695	390
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Olevia LT32HV"
	Device		"GeForce 7800 GS"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		"Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

I've spent a week trying to find a solution. Including a good deal of time getting mplayer all set up and working quite well with audio and video only to find the DVDnav barely works and bugs out often.

Any help in solving this would be greatly appreciated.

---

### Post by tramir on 2008-08-28
Hey, did you manage to solve the problem with totem? I have a similar issue, though reversed: totem plays videos at half width... Could you please share your solution with me, maybe I can deal with my problem?

---

### Post by Themicles on 2008-08-28
I'm not sure where you got that I solved it, but I haven't. Aspect ratios only display correctly with the Gstreamer back-end to Totem, and MPlayer, but not the xine back-end to Totem.

---

### Post by Themicles on 2008-08-28
Apologies, I misread your message as "How" rather than "Hey,".

Really hoping to find a solution as it would be nice to not have to boot to Windows for watching DVDs with menu support, proper video, and ac3 passthrough. Right now it's pick any two of the three, but never all three. 

This computer is our entertainment center with only the TV, cable box, and surround sound receiver in additional devices. We do not use any stand-alone players for any media.

---

### Post by tramir on 2008-08-28
No problem. I'll post a bug on launchpad, maybe we'll have more luck. It seems like other people have had similar issues with totem. I'll let you know if somebody comes up with a solution.

---

