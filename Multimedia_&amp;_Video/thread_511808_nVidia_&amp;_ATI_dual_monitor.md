---
title: "nVidia &amp; ATI dual monitor"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by akilies on 2007-07-28
I've done quite a bit of research, and I've found numerous tutorials on this, but before I went mucking around in my config file, I wanted to triple check this.

Previously I ran a dual monitor setup with my 19" widescreen (Proview FV926W) on my ATI RADEON X1300 and my 17" CRT (Gateway EV730) on my system's on-board card (I also have an available nVidia GeForce 4 MX 4000 working in a PCI slot).

I've read the "How To:" here on the forums about Xinerama, TwinView, Merged Framebuffer, and BigDesktop, but none of these seem to fit what I want to use my monitors for which is:

I treat my 19" as my primary monitor, playing games, surfing the web, etc, while my 17" is a secondary for instant messaging, music players, and tutorials/other information needed for an application on my primary.

So, my question is: With what I want to use my monitors for, which do I want? Xinerama, TwinView, Merged FB, BigDesktop, or none of the above?

P.S.
Any help, please be as lament as possible. I'm still learning Ubuntu after a life-long use of Windows/Mac.

Thanks in advance for any help.

EDIT: Here is (what I think is) the relevant part of my xorg.conf

```
Section "Monitor"
	Identifier	"Gateway EV73"
	Horizsync	30.0	-	70.0
	Vertrefresh	50.0	-	160.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"fglrx"
	Videoram	64000
	Option		"UseFBDev"	"true"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Busid		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Gateway EV73"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection
```

---

### Post by MrHippocampus on 2007-07-28
Basically, twinview only works on a dual head nvidia card, bigdesktop and mergedfb only work on dual head ati cards. So your left with two options.

1. Have two Xscreens where you can run programs on either on but not be able to drag windows between them
2. Have two X screens which you can drag windows between. (Xinerama).

If you want to set either of them up youll need to post the "serverlayout" part of your xorg.conf

---

### Post by akilies on 2007-07-28
```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
```

---

### Post by MrHippocampus on 2007-07-28
this *should* give you two X screens with xinerama, to turn off xinerama just put a # in front of the "Option "Xinerama"" line.

```

Section "ServerLayout"
	Identifier	"Default Layout"
        screen 0 "aticonfig-Screen[0]" 0 0
        screen 1 "Default Screen" RightOf "aticonfig-Screen[0]"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
        Option "Xinerama" "true"
EndSection

```

---

### Post by akilies on 2007-07-28
After inputing that line, I receive the [EE]Screen(s) found, but none are configured error, or whatever it is. I'm gonna try and disable Xinarama and see if that fixes the problem.

---

