---
title: "ppracer runs on Windows ME but not on Ubuntu"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by vanadium on 2007-04-30
I have installed Ubuntu on a Pentium III with 256 mbytes of RAM\. It has an inboard Intel graphics, Intel 82815 CGC (Chipset graphics). Planet Pinguin Racer (ppracer) will not run properly on this computer, despite the fact that I got 3D acceleration working. It worked by changing the default depth to 16 in xconf.org.

~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI i815 20050821 x86/MMX/SSE

glxgears runs nice and smoothly

~$glxgears
1812 frames in 5.0 seconds = 362.304 FPS
1936 frames in 5.0 seconds = 387.097 FPS

yet ppracer runs very jerky, and the letters of the menu are not displayed properly. The command line complains:

[driAllocateTexture:636] unable to allocate texture

What am I to do? What am I to do? Don't tell me to go to Windows ME to play a classical open source game!

For the technical soul willing to delve more deeply into this matter, I post some relevant sections of xorg.conf

```

Section "Device"
	Identifier	"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107T"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"PHILIPS 107T"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
#		Modes		"1024x768@85" "1280x1024" "1152x864" "832x624" "800x600" "720x400" "640x480" "640x350"
		Modes		"1024x768@85" "1152x864" "832x624" "800x600" "720x400" "640x480" "640x350"
#		Virtual		1024 768
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768@85" "832x624@85" "800x600@85" "720x400@85" "640x480@85"
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

---

### Post by vanadium on 2007-05-02
Yes, it is the configuration of the graphics card. Also Neverball does not run properly. Yet, on this same computer, it worked correctly under Mandrake (hint: this was a shameless bump).

---

### Post by CarVac on 2007-05-26
GLXgears running smoothly isn't a good diagnostic for a game. For example, glxgears on my computer runs at 1500 FPS but ppracer runs at 80.
If your computer runs glxgears at 300 then ppracer will be at 16 FPS.

---

### Post by vanadium on 2007-06-06
I agree, but these diagnostics suggest that 3D would be working correctly, yet they do not when loading the games. The funny thing is that it worked correctly with Mandrake two years ago, and that this concerns an Intel card which has open source drivers.

---

