---
title: "GeForce2 MX400 and NO TV-out!!!"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by Marran77 on 2007-12-03
Can somebody please help me.
 I've been trying to configure my TV- out on a GeForce2 MX 400 card (Nvidia). I been looking on all possible forums but haven't found any answer.
Using Nvidia-settings I can get a picture, but it is scaled and in black and white.
Trying to modify the xorg.conf following different HOWTOs haven't given any result att all!
On some forum i found something about "sauration"- value or something like that. But I can't find anything about it in the nvidia-settings-GUI.

I installed the drivers for GeForce2 with Envy. 
I use composite cables and have a PAL-B tv.

I would really appreciate somehelp in this one.

My xorg.conf:


Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
	Option		"XkbVariant"	"nodeadkeys"
	Option		"XkbOptions"	"altwin:meta_win"
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
	Identifier	"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"TwinView"
	Option		"SecondMonitorHorizSync"	"30-50"
	Option		"SecondMontitorVertRefresh"	"60"
	Option		"TwinViewOrientation"	"Clone"
	Option		"MetaModes"	"1024x768@1024x768, 1024x768@1024x768"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Ventura 150A"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Ventura 150A"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1280"	"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by cipher_nemo on 2007-12-03
Are you using an s-video connector for the second monitor/TV, or are you using a second VGA port?

If using an s-video, is it a proprietary dongle or a direct s-video (ie: 4-pin) connection? Have you tried another cable? Getting an image in gray-scale could be a configuration issue, but I'd be leaning towards a cable issue.

---

### Post by Marran77 on 2007-12-04
To the TV- out I have connected a composite cable with a scart connection in the other end. Using NVTV I can get a picture in color, but with a really bad resolution and that picture is also scaled.
I have been trying with an S- cable too, but can't get any picture at all using Nvidia- settings, and only in B&W using NVTV.

So I doubt it is the cable, or maybe Nvidia- settings can't see which type of cable I'm using...

Anyway, thanks for the reply

---

### Post by cipher_nemo on 2007-12-04
> **Marran77 said:**
> composite cable... Using NVTV I can get a picture in color, but with a really bad resolution and that picture is also scaled. (...) S- cable ... only in B&W using NVTV.

So you can only get B&W with NVTV while using an s-video cable, and color (but poor quality) with NVTV while using a composite connection?

With the s-video, have you tried 800x600 or 640x480 resolutions? Some TVs (non-HD/fullscreen) will look awful with 1024x768 and higher.

Yet, you may still have a configuration or compatibility problem. When you mention NVTV, are you using this?: [http://sourceforge.net/projects/nv-tv-out/](http://sourceforge.net/projects/nv-tv-out/) If so, some of the suggestions here might help: [http://sourceforge.net/forum/forum.php?thread_id=1372423&forum_id=105850](http://sourceforge.net/forum/forum.php?thread_id=1372423&forum_id=105850).

---

### Post by Marran77 on 2007-12-04
Yes, that's the NVTV I'm talking about. I looked at the link's but I can't say I'm able to follow the advices. I'm kind of new to Linux. Don't really know how to go through with anything like that without risk to mess anything up. 
But my TV do have a Chrontel chip, but 7500. And I have tried with an S- cable in different lower resloutions... But no, no, it won't work either.

When looking around a little more I have understood that I have a different version of nvidia-settings than most. My version lack the ability to set the saturation, which seems to be an option on newer versions. But I got mine from the repositories, I don't know where else to look.

---

### Post by cipher_nemo on 2007-12-04
I'd suggest at least uninstalling the previous version and installing the newer one. As for the directions they mention, they're all terminal-window commands. It might help to post your issue there and see if someone familiar with that project can walk you through troubleshooting. I don't have enough experience with it to do so. May be someone else here can help?

---

### Post by Marran77 on 2007-12-10
Solved. I have to put the resolution to 800x600, then I get a good picture (not scaled). Still the picture is in B&W though. But at least now I can use NVTV after having put the resolution to 800x600 and get a fearly good picture. 

But I'm going to continue my investigations. Cause clearly GeForce2 can put out the picture in color, but not through Nvidia-settings.

---

