---
title: "ATi AGP X1650 Major problem"
date: 2008-04-29
forum: Multimedia Software
---

### Post by SirZolofto on 2008-04-29
First of all, I've been using Ubuntu from Breezy, and I enjoy it a lot.  I recently upgraded to the much anticipated 8.4.  I see huge differences between the 2.  I never had a problem with ubuntu on my very old laptop (HP Omnibook 6000) and the video chipset (ATi Rage Mobility 8MB) 

I got this machine to run on Ubuntu 8.04, and instantly installed Fluxbox and the ATi restricted drivers.  At first, the ATi drivers made my screen not show up at all, and I recovered and went back to the normal drivers that was originally supplied.  ran at a max of 1280x1024, but with xrandr I got it to 1600x1200, but had to set it each time I had to set it each time I restarted.  

So I went back, and now I am trying to figure out this mess.  I installed and uninstalled these drivers about 3 times now, using several methods.  Ubuntu install, which basically enabled it after it installed.  Then tried the 2 methods described on the ATi "Unoffical" driver wiki.   Each one I keep getting strange errors, and things I shouldn't see.  

I'll describe the entire problem:

I start up the machine, instantly I see problems.  The loading bar underneath the "Kubuntu" starts to flicker when it bounces back and forth.  The loading bar hits 100%.  The splash screen disappears, and the console appears.  Stating me to login.  The screen flickers twice.  Goes back to the console, then brings up the main screen with a cursor.  The computer makes several high pitched beeps, and the screen artifacts on the top and bottom. 

It drops back into the console, then quickly goes back to the artifacting and flickering.  Ubuntu then comes up with a window stating I am in low resolution mode.  So I go and reconfigure everything.

Information:
Monitor: CPD G500 (Sony Trinitron Multiscan G500)
Video: I tried all of them.  :(

It brings me into the login screen, and I log in.  
I am down in 800x600, what looks to be 16bit color.  I go back, and try to set the resolution, highest now is 800x600 (Used to go up to 1600x1200 under xrandr, 1280x1024 that can be set in gnome resolution).  

I tried sudo dpkg-reconfigure xserver-xorg.  Got nothing, wouldn't even let me reset my video properties. (Breezy did this, not sure if there was a change since that release.  Taking it there is though).  

Some unique problems I receive:
under DISPLAY=0
It says something along the lines that It couldn't open the display. 
fglrxinfo tells me either that the mesa is indirect rendering.  
Or tells me the display is null.  

I go into my xorg.conf, and everything seems fine to me.  Why the hell is the thing not loading it?

I would LOVE to have a quick response that could fix the issue.  
It seems to be a hit or miss for many people out there.  
Right now I am extremely disappointed with hardy right now.  Breezy worked, I am sure the previous distributions do as well.  

I would be satisfied without all the fancy effects and 3d rendering for a week.  Just to get my 1600x1200 back, and atleast 24b color.  But I know how ATi does things.  Slowly, and half-assed.  Almost ditching the entire linux dream on this computer.  

Back on windows right now... 
Hopefully a fix, or some hope... Vesa (or whatever they are called) refuse to return to their normal state again.


if it comes to any good use:
[QUOTE=xorg.conf]Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:2:0:1"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Sony"
	Modelname	"Sony CPD-G500"
	Horizsync	30.0-121.0
	Vertrefresh	48.0-160.0
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
  modeline  "1856x1392@75" 288.0 1856 1984 2208 2560 1392 1393 1396 1500 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "1920x1440@75" 297.0 1920 2064 2288 2640 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
  modeline  "2048x1536@75" 340.48 2048 2216 2440 2832 1536 1537 1540 1603 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1600x1200@85"	"1792x1344@75"	"1600x1200@70"	"1792x1344@60"	"1600x1200@75"	"1856x1392@60"	"1600x1200@60"	"1856x1392@75"	"1600x1200@65"	"1920x1440@60"	"1400x1050@75"	"1920x1440@75"	"1400x1050@60"	"2048x1536@60"	"1280x960@75"	"2048x1536@75"	"1280x1024@60"	"1280x1024@85"	"1280x960@85"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:2:0:0"
	Driver		"fglrx"
	Screen	0
	Vendorname	"ATI"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1600x1200@60"	"1600x1200@75"	"1600x1200@65"	"1600x1200@70"	"1400x1050@75"	"1600x1200@85"	"1400x1050@60"	"1792x1344@75"	"1280x960@75"	"1792x1344@60"	"1280x1024@60"	"1856x1392@60"	"1280x1024@85"	"1856x1392@75"	"1280x960@85"	"1920x1440@60"	"1280x960@60"	"1920x1440@75"	"1280x1024@75"	"2048x1536@60"	"1152x864@75"	"2048x1536@75"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Sony"
	Modelname	"Sony CPD-G500"
	Horizsync	30.0-121.0
	Vertrefresh	48.0-160.0
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
  modeline  "1856x1392@75" 288.0 1856 1984 2208 2560 1392 1393 1396 1500 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "1920x1440@75" 297.0 1920 2064 2288 2640 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
  modeline  "2048x1536@75" 340.48 2048 2216 2440 2832 1536 1537 1540 1603 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection[/QUOTE]

Some specific specifications about the video card:
Radeon x1650 512MB AGP 8X (@8)
Chipset: RV530XT2

The OS is Ubuntu 8.04 Hardy Heron.  (KDE Installed, therefor Kubuntu apparently)

---

### Post by SirZolofto on 2008-04-29
I hear the x1650pro agp works under ubuntu.

So why is it not working for me?  Help!

---

