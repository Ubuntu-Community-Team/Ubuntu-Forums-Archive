---
title: "tv-out on GM965"
date: 2008-05-06
forum: Mythbuntu
---

### Post by max69 on 2008-05-06
Hello,
I've installed mythbuntu on my laptop but for the life of me I cannot get the TV-out to get properly. I would like to either use my laptop display and TV each in their respective resolution. If that is not possible or too complicated I would just like to use the TV only. At the moment when I boot with the tv plugged in I do not get anything on the TV and a weird desktop on the laptop with a XFCE wallpaper instead of mythbuntu on the whole of the screeen but the top panel stops at about 2/3 of the width of the screen. It is the same for fullscreen windows. My Xorg.conf file looks very weird with very little in it. I also got some info on my TV specs through my windows partition.
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```
```
ntel(R) Graphics Media Accelerator Driver for Mobile Report





Report Date:		05/06/2008

Report Time[hr:mm:ss]:	15:16:12

Driver Version:		6.14.10.4906

Operating System:		Windows XP* Professional, Service Pack 3, v.3264 (5.1.2600)

Default Language:		English

DirectX* Version:		9.0

Physical Memory:		3061 MB

Minimum Graphics Memory:	8 MB

Maximum Graphics Memory:	128 MB

Graphics Memory in Use:	10 MB

Processor:		x86 family 6 Model 15 Stepping 10

Processor Speed:		2193 MHZ

Vendor ID:		8086

Device ID:		2A02

Device Revision:		03





*   Accelerator Information   *



Accelerator in Use:		Mobile Intel(R) 965 Express Chipset Family

Video BIOS:		1471.0

Current Graphics Mode:	1280 by 800 True Color (60 Hz)







*   Devices Connected to the Graphics Accelerator   *





Active Notebook Displays: 1

Non Active Televisions: 1





*   Television   *



Monitor Name:		Generic Television

Display Type:		Analog

Gamma Value:		1.0

DDC2 Protocol:		Supported

Maximum Image Size:	Horizontal: Not Available

			Vertical:   Not Available

Monitor Supported Modes:

640 by 480 (60 Hz)

720 by 480 (60 Hz)

720 by 576 (60 Hz)

800 by 600 (60 Hz)

1024 by 768 (60 Hz)

Display Power Management Support:

	Standby Mode:	Not Supported

	Suspend Mode:	Not Supported

	Active Off Mode: Not Supported





*   Notebook   *



Monitor Name:		Plug and Play Monitor

Display Type:		Digital

Gamma Value:		2.20

DDC2 Protocol:		Supported

Maximum Image Size:	Horizontal: Not Available

			Vertical:   Not Available

Monitor Supported Modes:

1280 by 800 (60 Hz)

Display Power Management Support:

	Standby Mode:	Not Supported

	Suspend Mode:	Not Supported

	Active Off Mode: Not Supported

Raw EDID:

00 ff ff ff ff ff ff 00 0e 14 15 14 00 00 00 00

29 11 01 03 80 21 15 78 0a 09 2d 9d 56 4f 90 27

21 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01

01 01 01 01 01 01 ea 1a 00 80 50 20 0d 30 18 20

13 00 4b cf 10 00 00 19 00 00 00 0f 00 20 20 20

20 20 20 20 20 20 6e 05 0f 00 00 00 00 fe 00 43

50 54 0a 20 20 20 20 20 20 20 20 20 00 00 00 fe

00 43 4c 41 41 31 35 34 57 42 30 35 41 20 00 ba



* Other names and brands are the property of their respective owners.##############################################################
```

And my xorg

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

My laptop is a Zepto Znote 6025wd with Mythbuntu hardy. The TV is a Philips 28pw6008/05.
Thanks in advance.

---

### Post by max69 on 2008-05-09
Should I post this in another section of the forum to have a greater chance of getting help as it does not seem to be mythbuntu specific (xorg) ?

---

### Post by Bill magee on 2008-05-25
Max69, I see that a couple of guys have asked for help in this forum for their intel GM965, but with no replies. There must be a better forum for these questions. Maybe the absolute beginner forum.

BTW, my xorg looks exactly like yours. I have not tried tv-out, but I am having trouble with a second monitor.

Good luck with your problem.

---

