---
title: "Working xorg.conf for intel 915/910 graphics w/ i810 driver"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by lp7413 on 2006-08-20
I just wanted to poste my xorg.conf file for the intel 810 driver, this is currently working about as good as it will get on the Dell Inspiron 6000 notebooks.  I still haven't found an option for i810 that will "clone" the actual desktop, so the orientation in this config is "TV" Below "LCD" .  Other available options to use are RightOf, LeftOf, Above, and Relative.
I hope this is of some help to you folks using the i810 and needing the Svideo / TV out to work half way decent. 

> Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

#Section "Extensions"
#	Option "Composite" "enable"
#EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"synaptics"
	Load	"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"	
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"      	"auto-dev"
	#Option         "LeftEdge"      	"1700"
	#Option         "RightEdge"     	"4900"
	#Option         "TopEdge"       	"1700"
	#Option         "BottomEdge"    	"4200"
	#Option         "FingerLow"     	"25"
	#Option         "FingerHigh"    	"30"
	Option          "MaxTapTime"    	"10"
	Option          "MaxTapMove"    	"20"
	#Option         "VertScrollDelta" 	"100"
	Option	        "HorizScrollDelta" 	"0"
	Option          "MinSpeed"      	"0.30"
	Option          "MaxSpeed"      	"0.45"
	Option          "AccelFactor"   	"0.0030"
	Option          "SHMConfig"     	"on"
	Option          "Repeater"		"/dev/ps2mouse"
EndSection

 Section "Device"
	Identifier "Intel Corporation Intel Default Card"
	Driver "i810"
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout" "TV,LFP"
	Option "TVStandard" "NTSC"
	Option "TVOutFormat" "SVIDEO" # "Composite" #"SVIDEO"
	Option "ConnectedMonitor" "TV"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier "LCD"
	Option "DPMS"
	Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Monitor"
	Identifier "TV"
	HorizSync 30-50
	VertRefresh 60
EndSection

Section "Screen"
	Identifier "LCD"
	Device "LCD"
	Monitor "LCD"
	DefaultDepth 24
	SubSection "Display"
	Depth 1
	Modes "1280x800"
	EndSubSection
		SubSection "Display"
			Depth 24
			Modes "1280x800"
		EndSubSection
	EndSection


Section "Screen"
	Identifier "TV"
	Device "TV"
	Monitor "TV"
	DefaultDepth 24
		Subsection "Display"
			Depth 24
			Modes "1024x768"
		EndSubsection
EndSection

Section "ServerLayout"
	Identifier "LCDandTV"
	Screen 0 "LCD"
	Screen 1 "TV" Below "LCD"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "Synaptics Touchpad"
	#Option "Clone" "On"
	Option "Xinerama" "True"
EndSection

Section "ServerLayout"
	Identifier "LCD"
	Screen "LCD"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
	InputDevice "Synaptics Touchpad"
EndSection

Section "ServerFlags"
	Option "DefaultServerLayout" "LCDandTV"
	#Option "DefaultServerLayout" "LCD"
EndSection

Section "DRI"
Mode 0666
EndSection

If you have any questions and would like a response in realtime, catch me on irc.freenode.com  in #linuxsociety  my IRC nick is ttyfscker,  good luck, also if you have any improvements feel free to post them!

---

### Post by foolsh on 2006-08-20
take a look at this persons xorg.conf says they have solved the problem of cloned desktop
[http://www.computing.net/linux/wwwboard/forum/28975.html](http://www.computing.net/linux/wwwboard/forum/28975.html)

---

### Post by lp7413 on 2006-08-21
> foolsh  	take a look at this persons xorg.conf says they have solved the problem of cloned desktop
[http://www.computing.net/linux/wwwbo...rum/28975.htm](http://www.computing.net/linux/wwwbo...rum/28975.htm)l

Yes, I have tried that xorg.conf, it works ok if you have 2 monitors, as for the TV part, it doesnt work right.  I might take the time to change some things in it like CRT to TV and the "None,CRT+LFP"  to "None,TV+LFP".  When I do I will post the results.  Thanks for the reply.

---

