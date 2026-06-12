---
title: "Sapphire HD 2600 Pro"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by Corgana on 2008-01-27
I can't get this card to work, Installed fglrx and everything and it always reverts back to vesa. I have no idea where to even begin, any advice?

In my xorg.conf it says "fail-safe monitor" what does this mean?

> Section "Files"
EndSection

Section "Module"
	Load		"GLcore"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

---

### Post by terminal on 2008-01-27
in terminal type sudo dpkg-reconfigure xserver-xorg and follow the process . Select fglrx as driver , rest of monitor settings should be detected itself . Have u compiled fglrx driver from source or using ubuntu restricted driver manager ?  I have hd 2600 pro and it doesnt work with fglrx driver in ubuntu gutsy ( old version ) so i manually compile the latest one . See [http://wiki.cchtml.com](http://wiki.cchtml.com) for complete installation guide .

---

### Post by Corgana on 2008-01-28
I used the restricted drivers manager, I'm at work- But I'll let you know how things go

---

### Post by Corgana on 2008-01-28
Ok, so I reconfigured it and my xorg.conf says I'm using fglrx, but when I look at the "screens and graphics" thing, it still says I'm using vesa, and cant change resolution or anything through that or the "screen resolution" settings.

is there a better link on how to compile the latest fglrx? I wasn't sure exactly what I was looking for there.

---

### Post by Corgana on 2008-01-30
bump?:confused:

---

### Post by phrygius on 2008-01-31
I have this exact card, and I used Envy (just last night, actually).

It successfully installed the driver, and I'm assuming all is well as far as the basic driver stuff goes.  I now get 1900x1080 (using an HDTV), and before, I was getting some lower 4:3 resolutions that were stretched.

I did this just before going to bed last night, and I did not try out accelerated 2D stuff, but I did notice that 3D seems to be broken. Blender is unusable due to flicker, and 3D screensavers do not display.  I'll have to test it out more tonight cause I'm currently at work.

It could be some configuration issues.  I've been reading that other Radeon users have fixed broken 3D by fiddling with conf files.

-phrygius

---

### Post by phrygius on 2008-02-01
Update: With my install of the ATI binary driver from Envy two nights ago, I simply turned off the compiz desktop effects, and everything seems to be working perfectly!

Video, Blender, and 3D screensavers work fine with no flicker!  I'm so happy that it was a simple fix.

So @Corgana, just install via Envy and turn off compiz and you should be good

-phrygius

---

### Post by Corgana on 2008-02-01
> **phrygius said:**
> Update: With my install of the ATI binary driver from Envy two nights ago, I simply turned off the compiz desktop effects, and everything seems to be working perfectly!

Video, Blender, and 3D screensavers work fine with no flicker!  I'm so happy that it was a simple fix.

So @Corgana, just install via Envy and turn off compiz and you should be good

-phrygius

Actually I did just that on my own last night and got it working, the only thing is "Screens and graphics" only shows one monitor, and I have two. Xinerama didn't seem to do the trick either. Is it hopeless to get an extended desktop working? or should I wait and see if there will be better support in the future for this card?

---

