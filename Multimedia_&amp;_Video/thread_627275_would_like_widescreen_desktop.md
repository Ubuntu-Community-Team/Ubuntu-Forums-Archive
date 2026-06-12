---
title: "would like widescreen desktop"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by Ranma187 on 2007-11-29
hello folks, this is my first time here and i need a hand. I have a projector (mitsubishi hd100u), and would like to view my desktop in widescreen. the current resolution looks great. (1024x768) but its fullscreen. my projector is native to 1024x768 so thats the best way to see it. i am using an ATI Radeon 9800 Pro 128mb video card with the open source ati drivers. it looks good and i can use the 3d effects which was a pain in the rear to get working until i switched to ubuntu studio. anyway, what do i have to do to set it for widescreen? screens and graphics messes everything up when i tell it i have a widescreen monitor. please help

---

### Post by Ranma187 on 2007-11-29
by the way i absolutely love linux. my computer has never been this sweet ever! it pooped out with windows and works great with ubuntu. im still working on a few things, (ie, widewscreen desktop.) but i am learning fast. thanks guys

---

### Post by chewearn on 2007-11-29
I'm confused about what you are asking.

1024x768 is 4:3 aspect ratio.  Wide screen is 16:9, where you need something like 1280x768, etc.  Your projector don't support this resolution, or does it?

---

### Post by Ranma187 on 2007-12-01
i guess i dont know the resolution breakdown. i use this projector for other things like xbox 360 and i tell it 1024x768 and widescreen and that works wonderfully. sorry for the mistake there, just goes to show i need a hand. is 1280x768 something i have to enable in xorg.conf by adding to the script cuz its not there right now.  that sounds like an easy fix if thats the case but im not sure exactly how to word that. my projector is native to 1024x768 but it can upscale so that resolution should be fine. please forgive any ignorance and help me out if you can. thanx

---

### Post by Ranma187 on 2007-12-01
once again, my mistake, i just worded that wrong. it is native to 1280x768. that resolution is perfect. i just need to know how to use that res.

---

### Post by chewearn on 2007-12-03
Apologies, for not replying earlier.

Unfortunately, I just noticed you have ATI Radeon, with open source ATI driver.  I'm not familiar with ATI, only use nVidia.

Just want to know also, are you referring to single display set-up, or dual display?  I ask because you want to use a projector, and normally a projector is used as a secondary display.

If it's single display, I would think you just need to add 1280x768 mode to the Section "Screen", Subsection "Display".  I could be wrong though; like I said, I'm not familiar with ATI.  Anyone else in the forum want to take a shot?

---

### Post by Ranma187 on 2007-12-04
right now i use my projector as a single display, i use a wireless keyboard and mouse so it works out great. in the future i would like to use my lcd screen again with a dual monitor setup, but one thing at a time, and there doesnt seem to be great support for that right now. More important to me right now is getting my one desktop to be widescreen. i tried adding 1280x768 into the screen section by replacing the 1024's with 1280's and saving but it didnt change anything when i rebooted x. do i have to activate this newly saved xorg.conf file or something like that. this all seems like a simple thing but i am running into walls everywhere i go.


P.S. no appologies necessary astalavista, im just glad someone is paying attention. thanks

---

### Post by Ranma187 on 2007-12-04
this is what my xorg.conf looks like right now. (last version i saved)





Section "Files"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Mitsubishi"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"Mitsubishi"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x768@75"	"1280x768@70"	"1280x768@85"	"1280x768@60"	"832x624@75"	"1152x864@75"	"800x600@60"	"1280x1024@75"	"800x600@85"	"1280x960@60"	"800x600@75"	"1280x1024@60"	"800x600@72"	"1280x960@75"	"800x600@56"	"1400x1050@60"	"640x480@85"	"1600x1200@60"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	1
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by chewearn on 2007-12-04
I see a lot of modelines.  Not sure if this is autogenerated, or you add them yourselves?

While waiting for a more knowledgeable person to step in, I will try to suggest a few things that I know of.

First, did you already try to recreate xorg.conf by this command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

In the third question (I think) you can specify the resolutions to add.  Make sure the 1280x768 is selected.  Backup your existing xorg.conf before doing this, in case you need to revert.

Second, You can also take a look at the file: /var/log/Xorg.0.log

This might give you some hints on what is going on with your graphics card and resolution detection.

---

