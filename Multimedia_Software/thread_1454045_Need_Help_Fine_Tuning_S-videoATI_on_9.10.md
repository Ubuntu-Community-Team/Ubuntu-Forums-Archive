---
title: "Need Help Fine Tuning S-video/ATI on 9.10"
date: 2010-04-14
forum: Multimedia Software
---

### Post by BJ_Covert_Action on 2010-04-14
Hello All,

This post, hopefully, represents the final bit of help I will need to get my PC-TV setup in my living room properly configured. I already detailed some of my travails in _[these](http://ubuntuforums.org/showthread.php?t=1452477) [two](http://ubuntuforums.org/showthread.php?p=9120204#post9120204)_ threads (posted for reference only).

Essentially, what I am attempting to do is set up an older PC with a Radeon 9600 video card chipset in it with xubuntu 9.10. I would like to attach this PC to my rear projection tv (Sony KP-48S75) via an S-video cable and use this TV as the primary and only monitor for the system. At one point, I had Ubuntu 8.04 hacked onto this same hardware fulfilling this role decently. However, due to some carelessness on my part, the system became unstable and I decided to start anew (random crashes, lots of X freezes, dependency issues, screwing too much with my sources.list and so on). So, that said, I installed Xubuntu 9.10 on the PC and had it hooked up to both an LCD monitor and the TV via S-video. Upon boot, both outputs worked, though X only rendered on the LCD and not the TV. Thus, I dug and researched and found that by putting a bunch of xrandr commands into my gdm start script I could finagle the TV into displaying my output, mostly. The commands I used to get the S-video out work (and, therefore, pasted into my */etc/gdm/Init/Default* script) follow:

```

xrandr --output S-video --set load_detection 1
xrandr --output S-video --set tv_standard ntsc
xrandr --output S-video --set tv_horizontal_position -2
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xrandr --output S-video --rate 60
xrandr --output VGA-0 --off

```

You'll notice I do a few things in those commands. First, I set load_detection to 1 in hopes of enabling automatic S-video connection detection (this isn't working). The next interesting bit is my commanding the horizontal position. The reason I had to do this is, because, upon getting the S-video output to render, the picture rendered to the right-hand side of the screen, deprecating the furthermost bits (for instance, I cannot see the shutdown icon in the upper right hand corner). Setting the horizontal position to -2 allowed me to shift the display to the left a bit, but, to my surprise, the right hand side still deprecates and I am just left with a black column on the right hand side. Now, I did read something that said this could be a rates issue, hence the commanded rate of 60 (my video cards spec) in the above commands. However, that didn't seem to fix the problem. So question #1, does anyone know why the right side of my screen deprecates? If so, do you have any fixes to suggest?

Question 2 has to do with the screen indexing. If I run a xrandr command with no options, I see VGA-0 indexed as Screen 0. I also see the S-video listed as disabled (even though I see it rendering on the TV right in front of me). Finally, I notice that, under the VGA-0 section, there is a screen size listed, as well as several resolution modes with many parameters following them (like 800x600 72.2*+  75.0 .... some other stuff). However, under the S-video section all I see is one mode with one small bit after it (800x600 72.2*). This smacks of suspicion to me and makes me think it might be related to the right side of my screen being deprecated. My wager is that I need to tweak some modelines in the S-video output so that it is more in sync. However, I do not know the syntax for modeline editing and, since the S-video screen isn't even detected, I am not sure I really can edit these options. Does anyone know why my S-video output would continue to be listed as disabled even when its running? Furthermore, can anyone tell me why no screen index is given to the S-video output (I only see screen 0 attached to VGA-0, no screen 1 for S-video)? Any help on this issue would be particularly relevant because I think I need the screen indexed properly in order to use the xvattr command later in order to allow xv overlays to function on the proper screen.

Finally, I do have a xorg.conf file loaded in /etc/X11 that is mostly hacked together stuff I used trying to get this to work in the first place. Would this conflict with the xrandr setup? Which options override which?

I know this is a lot of requests for help at once, and I will keep researching. However, I hope to get some answers to these questions soon as I've been hacking at this for 5 days straight now with no input on any of my other help requests and I would really like someone with some more knowledge to help guide me on this.

Thanks ahead of time for anything anyone can provide. 

Best of luck to you all. :)

---

### Post by BJ_Covert_Action on 2010-04-15
24 Hour bump. I did  bit more tweaking today and I  think I have the xorg.conf file  and xrandr commands in the GDM Default script pretty well balanced. However, I still can't get the full screen rendered on the TV. I posted my xorg.conf file contents and GDM Defaut script below. Please let me know if you can help guys, I've posted on this  subject  a few times now and am getting disappointed at the lack of help.

*xorg.conf*
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"dead"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Radeon_9600"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"TVDACLoadDetect" "TRUE"
	#Option		"XAANoOffscreenPixmaps"
	Option		"Monitor-S-video" "SVid_Out"
	#<ENABLE_VGA_HERE>
	#<ENABLE_SVID_HERE>
EndSection

Section "Monitor"
	Identifier	"VGA-0"
	#Option		"Ignore" "true"
	#Horizsync	31.5	-	35.1
	#Vertrefresh	50.0	-	61.0
EndSection

Section "Monitor"
	Identifier	"SVid_Out"
	#Modeline	"640x480_54"  21.00  640 648 712 784  480 481 484 496  -HSync +Vsync
	Modeline	"800x600_54"  33.69  800 824 904 1008  600 601 604 619  +HSync +Vsync
	Modeline	"800x600_60"  38.22  800 832 912 1024  600 601 604 622  +HSync +Vsync
	#Modeline	"800x600_61"  38.22  800 856 976 1040  600 637 643 666  +HSync +Vsync
	Option		"PreferredMode" "800x600_60"
	DisplaySize	952 724
	Option		"Above" "VGA-0"
	Option		"Enable" "true"
	#Mode		"800x600_54"
	#Horizsync	31.5	-	35.1
	#Vertrefresh	50.0	-	61.0
EndSection

Section "Screen"
	Identifier	"TV_Screen"
	Device		"Radeon_9600"
	#Monitor		"Rear_TV"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		#FbBpp	32
		#Modes	"800x600" "640x480"
		#Virtual 800 600
		Virtual	800  1200
		#Virtual 3000 2000
	EndSubsection
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		"TV_Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

*Display Commands in /etc/gdm/Init/Default*
```

xrandr --output S-video --set load_detection 1
xrandr --output S-video --mode 800x600_60
xrandr --output S-video --crtc 1
xrandr --output S-video --set tv_horizontal_position -2
xvattr -a XV_CRTC -v 1

```

Cheers,
Brady

---

### Post by molar on 2010-05-13
will appreciate help on this also.

---

