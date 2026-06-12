---
title: "Need help, searched"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by vwfix on 2008-01-24
I am trying to set up dual monitors with a nvidia 8400 GS
got the nvidia restricted drive set up, for some reason the system only sees vga and not the dvi, if I try to boot up with just the dvi it still does not work.
nvidia-settings does not see the second screen also.
and when I try to click the save xorg.conf in nvidia-settings i get this message

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Can someone help me configure the xorg file or give me a xorg file that will work, I am trying to run a dell 1907fp on the vga which works fine and a viewsonic  VA2012wb on dvi and neither monitors get detected by the dvi.
Need help desperatly.:confused:

---

### Post by vwfix on 2008-01-24
Well I finally got the twinview to work, the only issue now is the viewsonic will not go past the 640 resolution can someone look at xorg.conf and correct my mistake, also any clues why the nvidia-settings fails to save the xorg.conf file

> 
Section "Device"
	Identifier	"0 nVidia Corporation G80 [GeForce 8400 GS]"
	Driver		"nvidia"
	Screen	0
	Option		"TwinView"	"True"
	Option		"TwinViewOrientation"	"RightOf"
	Option		"UseEdidFreqs"	"True"
	Option		"MetaModes"	"1280x1024,1280x1024; 1024x768,1024x768"
	Option		"UseDisplayDevice"	"CRT"#replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
	Option		"ConnectedMonitor"	"DFP, CRT"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"1 nVidia Corporation G80 [GeForce 8400 GS]"
	Driver		"nvidia"
	Screen	1
	Option		"TwinView"	"True"
	Option		"TwinViewOrientation"	
	Option		"UseEdidFreqs"	"True"
	Option		"MetaModes"	"1280x1024,1280x1024; 1024x768,1024x768"
	Option		"UseDisplayDevice"	"DFP"#replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
	Option		"ConnectedMonitor"	"DFP, CRT"
EndSection


Section "Monitor"
	Identifier	"DELL 1907FP"
	Option		"DPMS"
	Horizsync	30-100
	Vertrefresh	50-160
EndSection

Section "Monitor"
	Identifier	"DELL 1907FP 2"
	Option		"DFP"
	Horizsync	30.0 - 82.0 
	Vertrefresh	50.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"0 nVidia Corporation G80 [GeForce 8400 GS]"
	Monitor		"DELL 1907FP"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 nVidia Corporation G80 [GeForce 8400 GS]"
	Monitor		"DELL 1907FP 2"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Main Screen"
  screen 1 "Second Screen" rightof "Main Screen"
	Option		"TwinView"	"true"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"

---

