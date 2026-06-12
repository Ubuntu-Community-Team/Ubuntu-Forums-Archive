---
title: "Cropped screen + monitor powers off on resolution change"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by polkovnik on 2007-11-26
Hey guys! 
Just clean-installed Ubunty Gutsy from DVD. Video card and monitor was detected correct, BUT the screen goes down beyond the bottom border, so I can't see the bottom panel with a piece of bottom desktop area. Current resolution is 1280x1024. 
Another problem turned out when I tried to change the resolution, no matter to what, -- the screen went black and turned off (ctrl+alt+bcksp). Plus the refresh rate -- it indicates 85 Hz, but what I really see is pure 60! The cropped screen was there from when I booted from the liveDVD. Sometimes, if I drag something below the visible area, system freezes, leaving the only option of reseting computer.
 Here are some values from my current xorg.conf:
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R200 QM [Radeon 9100]"
	Boardname	"ati"
	Busid		"PCI:2:0:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 959NF/900NF/909NF/CN199A(P)"
	Horizsync	30-110
	Vertrefresh	50-160
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
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R200 QM [Radeon 9100]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1280x1024@85"	"1280x1024@60"	"1280x960@85"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@43"	"1600x1200@60"	"1024x768@60"	"1600x1200@75"	"1024x768@70"	"1600x1200@70"	"1024x768@75"	"1600x1200@85"	"1024x768@85"	"1792x1344@75"	"832x624@75"	"1792x1344@60"	"800x600@60"	"1856x1392@60"	"800x600@85"	"1920x1440@60"	"800x600@75"	"2048x1536@60"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection 

My system is:
CPU AMD Athlon 1.1 Ghz
DDR 512
Mother Asus A7N8X v2.0 with nVIDIA nForce2 Ultra 400
Video RADEON 9100 SERIES (integrated)
Display Samsung SyncMaster 959NF (19" CRT)
Would greately apreciate some help.

Updated:
I did a reconfigure of the x-server.
Well now the refresh change IS possible if swiched to the lower refresh rate on the same resolution and then back to the maximum(tricky one), (In the Administration->Video&Resolution menu item), some times cursor disapears(?). I couldn't change the resolution itself without having to crash Xserver. Bad news is that it all is canceled when I log off or restart, and I'm back to my 60Hz and cropped screen.
Tried to install ATI driver. Downloaded one from the ATI/AMD site. My current supported version is 8.28.8. But the installation failed with the 'Bad substitution' error. Googled for that one and searched the forums, -- nothing that seemes to help me out with that one. Plus -- The "Desktop Effects" menu item is gone now, and all the effects enabled by default are now turned off. 
It seemes that my Ubuntu is slowly dying :) Help it, please!

---

### Post by zbyszek_zbl on 2007-11-26
May be you should try to install new drivers with envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It is small application which automatically installs ati or nvidia drivers with all needed dependencies and basic configuration - for me it has always worked fine. After installing envy first remove with it all ati drivers that install new one.

---

### Post by polkovnik on 2007-11-26
I've ran into it couple of hours ago, but didn't pay any attention, 'cause thought it is for the nVidia stuff. Thanx, I'll try that.
Please tell me -- maybe it is better to fix up some network connection first, and then ask Ubuntu kindly to decide everything on its own via the internet, (couldn't bring up that one either) if this is the case?

---

### Post by polkovnik on 2007-11-28
Nope, no luck with that one either.
The resolution stays the same, refresh too. Still cropped bottom  of the screen, still "Destop Effects" gone missing, still so desperate. Plus windows and data partitions don't mount on system startup anymore. Well I DO know how to mount them manually, but that still gives me dissapointment with Ubuntu. If you find some time please give me a hand with this. I would really apreciate one right now.

---

### Post by polkovnik on 2007-11-29
Case may be considered closed. 
To hell with ubuntu! I'm going back to SuSE, it is among the best in recognizing hardware (for a change).
Good bye, thanx for nothing.

---

