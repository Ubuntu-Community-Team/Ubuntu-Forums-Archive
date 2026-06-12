---
title: "sisusb external  USB VGA Adapter"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by santoshssu on 2007-09-19
Hi, 
My xorg.conf is as below , I am not able to get the display on my external monitor.
I am using USB2VGA external adapter and sisusb driver.
Please help me on this, I am trying to get the dual mode

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load    "record"
	Load	"freetype"
	Load    "speedo"
#	Load	"glx"
	Load	"int10"
	Load	"vbe"	
	Load    "type1"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection


############# Monitor Section #########

Section "Monitor"
	Identifier	"LaptopMonitor"
	Option		"DPMS"
	VendorName   "Monitor Vendor"
	ModelName    "My Laptop device"
	VertRefresh  60-75
	HorizSync    30-90

EndSection

Section "Monitor"
	Identifier      "ExternalMonitor"
	VendorName  "Monitor Vendor"
	ModelName   "My VGA monitor"
	Option          "DPMS"
	HorizSync       28-51
	VertRefresh     43-60
	ModeLine "1920x1200" 154.0 1920 1968 2000 2080 1200 1203 1209 1235
EndSection


################## device Section #############
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 	 	0
	Option		"MonitorLayout" "DFP,LFP"
	Option		"DevicePresence" "yes"
EndSection


Section "Device"
	Identifier "SiS USB2VGA"
	#VendorName "SiS"   # Value does not matter
	#BoardName  "SiS"   # Value does not matter
	Driver     "sisusb"
	BusID     "PCI:0:2:0"
	#Option "ForceCRT1" "on
	#Option "ForceCRT2Type" "VGA"
#	BusID     "PCI:00:1d.3"
	Screen	    1
	Option		"MonitorLayout" "DFP,LFP"
	Option		"DevicePresence" "yes"
EndSection

######################## Screen Section #########
Section "Screen"
	Identifier	"Screen1"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"LaptopMonitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier      "Screen2"
	Device		"SiS USB2VGA"
	Monitor         "ExternalMonitor"
	DefaultDepth    24
	SubSection "Display"
		Depth           1
		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth           4
		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth           8
		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth           15
		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth           16
		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth           24
		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


#Section "Screen"
#	Identifier "screen1"
#	Device     "SiS USB2VGA"
#	Monitor    "Generic"
#	DefaultDepth 16
#	SubSection "Display"
#		Depth     16
#		Modes     "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth     8
#		Modes     "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth     24
#		Modes     "800x600" "640x480"
#	EndSubSection
#EndSection

#################################################################3

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Screen1" 0 0
	Screen 	"Screen2" 
	#Screen 1	"Screen2" RightOf "Screen1"
#	Option		"Xinerama" "On"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"cursor"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


Section "DRI"
	Mode	0666
EndSection

---

### Post by daller on 2007-09-19
Try this wikipage:

[https://help.ubuntu.com/community/USB2VGA?highlight=%28sisusb%29](https://help.ubuntu.com/community/USB2VGA?highlight=%28sisusb%29)

---

### Post by santoshssu on 2007-09-19
Thank  you very much for the instructions.
I am able to get the external monitor working.

I am newbee in this .

Please help me in getting up 2 X servers running .
one is already running for main display on  mode :0

and another one I want to start on mode :1

---

### Post by daller on 2007-09-20
What do you see on your second display? - nothing?

---

### Post by santoshssu on 2007-09-26
Hi Daller,
   I am able to see the second display with the above setting,
 but I was trying to explore more on this, 
Like starting two X servers , .... please help me if you have any idea on this.

Thanks in advance.

---

