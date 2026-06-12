---
title: "'strange' stretched/squashed display"
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by andrewsawyer on 2005-12-14
Sorry - I don't know how else to describe it!

I have two monitors, one is a Philips 17PF9945 17" widescreen, the other a Polyview 17" 4:3.  The widescreen resolution is set as 1280x768, and the 4:3 is set as 1024x768.

For some reason, when looking at text on the widescreen monitor, the width of it seems to be slightly deformed - I'm not quite sure how else to describe it, so I have attached a couple of png files.  *976.png is on the widescreen, *977.png is after the same text box has been dragged over to the 4:3.  I've not just done a screen print, as this seems to be a monitor issue, and doesn't show up in a screen print - I've taken the pictures with a digital camera.

If it helps, I'm using a VGA connection to the Widescreen, and I'm also using the nVidia drivers.  The issue was there **before** I enabled TwinView, so it is not a setting that I have done while trying to set up the twin monitors.

If I have the widescreen set as 1024x768, the issue corrects itself (although obviously everything looks wrong because its a widescreen).

Before the nVidia drivers were installed, the system outputted to only my 4:3.  Then when I installed the nVidia driver, the system only outputted to my 16:9.  It also then showed this issue.  Then after that, I enabled TwinView which did not increase or decrease the severity of the problem.

If you can help me, please let me know!

Andy

---

### Post by andrewsawyer on 2005-12-14
I'll explain it a bit better - take the letter 'l'.  It is 2px wide.  If I write the letter 'l and display it on my 16x9, it may or may not display as 2px wide. It may also display as only 1px wide.  If it is displaying as 2px, and I drag it horizontally across the screen, it will flick between 1px and 2px width.  It is as if some of the vertical 'lines' are missing.

Looking at a picture will be fine (but then it is still spanned proportionally across the whole screen [1024px], so I guess this would be expected.

From moving a vertical line horizontally across the screen, I think I have worked out that every 5th pixel is missing (or not shown).

Hope that helps with my previously poor explantation.

Andy

---

### Post by stuporglue on 2005-12-14
Is it an LCD screen, and is it at it's native resolution? 

I had a laptop screen looking like that. X was defaulting to 800x600, but the screen couldn't do 800x600 propperly, so some pixles were doubled, and some missing. Switching to that screen's native resolution (1024x786, in my case) fixed the problem.

---

### Post by Joeak on 2005-12-14
Post a copy of your xorg.conf file.  What is your system type, video card, and amount of video memory, as well?

The visual problem you describe is called "dithering", where something (your monitor) is adjusting the video output to take up the whole screen, but Ubuntu is probably only generating 1024x768 or something, so the LCD mangles it to make it fit.

Aren't LCD's wonderful?  This problem didn't happen with CRT's.  (Although you still would like to use the higher native resolution anyway.)

---

### Post by andrewsawyer on 2005-12-14
xorg.conf (only related section):
```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	VendorName 	"Videocard vendor"
	BoardName 	"NVIDIA GeForce 6600 GT"
	Option		"ConnectedMonitor" "CRT, dfp"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline	"1280x768@60" 83.91 1280 1312 1624 1656 800 816 824 841
	Option		"TwinView" "true"
	Option		"TwinViewOrientation" "RightOf"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Option		"MetaModes" "1280x768,1280x1024;1280x768,1024x768;1280x768,NUL;1024x768,NULL;NULL,1280x1024"
		Option     	"SecondMonitorHorizSync"   "30-82"
    		Option     	"SecondMonitorVertRefresh" "56-76"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
    Option      "Xinerama"      "false"
EndSection

```

Note: In the SubSection "Display" Option "MetaModes", the first option (1280x768,1280x1024) is not used - I haven't worked out how to get this (or if it's even possible) yet.  So the system is loading with the second option (1280x768,1024x768).  This shows in System > Preferences > Screen Resolution as 2304x768.  That being 1280+1024=2304.

Checking the details from [here]("http://reviews.designtechnica.com/review707_specs3534.html") shows the following details about my 16:9 monitor:

```
Supported Display Resolution
Computer formats :  1024 x 768, 60HZ, 1280 x 768, 60Hz, 800 x 600, 56,60,72,75,85 Hz, 640 x 480, 60, 72,75, 85 Hz
Video Formats :  1280 x 720p - 3Fh, 1920 x 1080i - 2Fh, 640 x 480i - 1Fh, 640 x 480p - 2Fh
```

The details of my system are as follows:

AMD Athlon 3800+ 64bit Dual Core
2Gb Ram
Albatron GForce 6600GT graphics card w/ 128Mb

The 16:9 is coming from the standard VGA (CRT) port and the 4:3 is coming from the DVI (DFI) port.

Many thanks for getting back to me on this.  I just hope someone is able to help me out!

Andy

---

### Post by andrewsawyer on 2005-12-16
Ping...

---

### Post by andrewsawyer on 2005-12-28
Does anyone have any info on this?  Is it possible to have 1280x768 in one screen and 1280x1024 in the other?

Cheers,

Andy

---

