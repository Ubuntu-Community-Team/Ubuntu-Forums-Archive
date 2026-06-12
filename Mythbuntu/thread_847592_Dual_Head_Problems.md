---
title: "Dual Head Problems"
date: 2008-07-02
forum: Mythbuntu
---

### Post by Tteddo on 2008-07-02
Hello! I have a dual head setup that was working perfectly in Mythbuntu 7.1 (the last one). I have a CRT on the analog, and a 52" TV on the digital output. The CRT was at 1024X768 and the TV was at HDTV (1920x1080) and they were 2 different desktops. I upgraded to 8.4 and now (after getting the video overlay to work) what happens is it comes up with a cloned desktop, to the login screen. The displays are at the proper resolution, but cloned, then when I login it seems that XFCE is taking aver and forcing them both to 1280x1024 and ignoring what is in xorg.conf. I can't seem to find the settings for this.
Any ideas? My xorg.conf is below:

> #	Created By Tteddo
#	sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier	"Dual Head Layout"
	screen 0 "Screen0" 0 0
 	screen 1 "Screen1" leftof "Screen0"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"NoPM"	"0"
	Option		"blank time"	"0"
	Option		"standby time"	"0"
	Option		"suspend time"	"0"
	Option		"off time"	"0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"ctrl:nocaps"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Option		"ModelName"	"Mitsubishi"
	Option		"DPMS"	"true"
	Horizsync	30.0	-	95.0
	Vertrefresh	60.0	-	60.0
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"ModelName"	"Optiquest Q71"
	Option		"DPMS"	"true"
	Horizsync	30.0	-	90.0
	Vertrefresh	50.0	-	150.0
EndSection

Section "Device"
	Identifier	"Device0"
	Driver		"fglrx"
	Screen	0
	Option		"MonitorLayout"	"CRT,CRT"
	Option		"DesktopSetup"	
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Device"
	Identifier	"Device1"
	Driver          "fglrx"
	Screen	1
	Option		"MonitorLayout"	"CRT,CRT"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes		"1920x1080"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Device1"
	Monitor		"Monitor1"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes		"1024x768"
	EndSubSection
EndSection

---

### Post by Tteddo on 2008-07-07
*Bump* (that was my head!)
Anyone have any ideas?

---

