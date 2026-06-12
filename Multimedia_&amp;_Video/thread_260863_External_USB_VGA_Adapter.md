---
title: "External USB VGA Adapter"
date: 2006-09-19
forum: Multimedia &amp; Video
---

### Post by daller on 2006-09-19
Hi There,

Any ideas one how to get an external USB VGA adapter working?

here my lsusb output:

```

Bus 004 Device 002: ID 182d:0269
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

And dmesg (after inserting it):

```

[17181665.096000] usb 4-1: new high speed USB device using ehci_hcd and address 5
[17181665.228000] sisusb: USB2VGA dongle found at address 5
[17181665.228000] sisusbvga[133]: Allocated 8 output buffers
[17181665.360000] sisusbvga[133]: 8MB 1 ch/1 r SDR SDRAM, bus width 32

```

It's a "Sitecom CN-105"

Found this so far:

[http://www.winischhofer.at/linuxsisusbvga.shtml](http://www.winischhofer.at/linuxsisusbvga.shtml)

[http://www.nslu2-linux.org/wiki/HowTo/AddVGAAdapter](http://www.nslu2-linux.org/wiki/HowTo/AddVGAAdapter)

...but haven't got it to work!

**EDIT:**

Seems that Ubuntu has the driver out-of-the-box:

**sisusbvga**

Running "sudo modprobe sisusbvga" turns on the adapter, triggers my monitor (it's turning on)

Now I see a red border all around the display. (On the external monitor)

I think I have to set up the adapter in xorg.conf, but I have no idea how!

---

### Post by tseliot on 2006-09-19
> **daller said:**
> Hi There,

Any ideas one how to get an external USB VGA adapter working?

here my lsusb output:

```

Bus 004 Device 002: ID 182d:0269
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

And dmesg (after inserting it):

```

[17181665.096000] usb 4-1: new high speed USB device using ehci_hcd and address 5
[17181665.228000] sisusb: USB2VGA dongle found at address 5
[17181665.228000] sisusbvga[133]: Allocated 8 output buffers
[17181665.360000] sisusbvga[133]: 8MB 1 ch/1 r SDR SDRAM, bus width 32

```

It's a "Sitecom CN-105"

Found this so far:

[http://www.winischhofer.at/linuxsisusbvga.shtml](http://www.winischhofer.at/linuxsisusbvga.shtml)

[http://www.nslu2-linux.org/wiki/HowTo/AddVGAAdapter](http://www.nslu2-linux.org/wiki/HowTo/AddVGAAdapter)

...but haven't got it to work!

**EDIT:**

Seems that Ubuntu has the driver out-of-the-box:

**sisusbvga**

Running "sudo modprobe sisusbvga" turns on the adapter, triggers my monitor (it's turning on)

Now I see a red border all around the display. (On the external monitor)

I think I have to set up the adapter in xorg.conf, but I have no idea how!

I have never had a usb-vga adapter but I guess you can try this:

Add this to your xorg.conf:

```
Section "Device"
        Identifier "SiS VGA chipset"
        VendorName "SiS"
	BoardName  "SiS"
	Driver     "sis"
EndSection
```


and use it like you would with a graphic card.

You will have to use some options such as the ones which you can find in this example:
[http://www.winischhofer.net/sis/XF86Config-4.example](http://www.winischhofer.net/sis/XF86Config-4.example)

Then add a screen:

```
Section "Screen"
	Identifier "screen1"
	Device     "SiS VGA chipset"
	Monitor    "Generic|Generic LCD Panel"
	DefaultDepth 24
	SubSection "Display"
		Depth     16
		Modes     "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes     "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes     "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by daller on 2006-09-20
Thanks!

It turned out this way:

I had to add a DEVICE, a MONITOR and a SCREEN (and add screen to serverlayout)

My xorg.conf now look like this:

```

Section "Files"
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

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
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
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"WizardPen Tablet"
	Option		"SendCoreEvents"	"true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "2553"
        Option          "TopY"          "3958"
        Option          "BottomX"       "30649"
        Option          "BottomY"       "29892"
        Option          "MaxX"          "32739"
        Option          "MaxY"          "32745"

EndSection

Section "Device"
	Identifier	"Device[0]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	screen 0
	Option "NoLogo" "true"
EndSection

Section "Device" 
        Driver          "nvidia" 
        Identifier      "Device[1]" 
        Screen 1 
        Option          "TVOutFormat" "Composite" #or SVIDEO etc 
        Option          "TVStandard" "PAL-G" #or NTSC etc 
        Option          "ConnectedMonitor" "Monitor[1]" 
        BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Device"
        Identifier "Device[2]"
        VendorName "SiS"   # Value does not matter
	BoardName  "SiS"   # Value does not matter
	Driver     "sisusb"
EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #MONITOR
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Monitor" 
	Identifier "Monitor[1]" #TV
	HorizSync 30-50
	VertRefresh 60
EndSection

Section "Monitor"
	Identifier   "Monitor[2]" #SISUSBVGA
	VendorName   "Monitor Vendor" # value does not matter
	ModelName    "Monitor Model"  # value does not matter
	VertRefresh  50-75
	HorizSync    30-90
EndSection

Section "Screen"
        Identifier "Screen[0]"
        Device "Device[0]"
        Monitor "Monitor[0]"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"

		Depth		15
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Device "Device[1]"
        Identifier "Screen[1]"
        Monitor "Monitor[1]"
        DefaultDepth 24
        SubSection "Display"
               Depth 24
               Modes "1280x960_60"
        EndSubSection
EndSection

Section "Screen"
	Identifier "Screen[2]"
	Device     "Device[2]"
	Monitor    "Monitor[2]"
	DefaultDepth 16
	SubSection "Display"
		Depth     16
		Modes     "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes     "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes     "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
   	Identifier  "Simple Layout"
	Screen 0 "Screen[0]"
	Screen 1 "Screen[1]" RightOf "Screen[0]"
	Screen 2 "Screen[2]" RightOf "Screen[1]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "WizardPen Tablet" "AlwaysCore"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

The USB2VGA dongle now works! - Thanks!

It's on a Dell Inspiron 8600 (where I haven't succeeded getting my normal external monitor connection to work! - Any ideas?)

---

### Post by fh_scott on 2007-05-15
Between this thread and the one [ATI-Big Desktop]("http://ubuntuforums.org/showthread.php?t=301941") I was finally able to get my Inspiron 6400 to utilize the USB2VGA @ 1280x1024 and have the notebook's LCD panel to spread out to another 19" LCD @ 1280x1024.

Now if it just all worked with xgl...

Thanks for everyone's contribution.

-scott

---

### Post by santoshssu on 2007-09-18
Hi ,
 My xorg.conf is as below but then still I am not able to get the display on my external monitor.
I am using  sisusb driver.

Please help me on this, I am  trying to get the dual mode.

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
	Load	"glx"
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
	HorizSync       30-90 
	VertRefresh     50-75 
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
	VendorName "SiS"   # Value does not matter
	BoardName  "SiS"   # Value does not matter
	Driver     "sisusb"
	#BusID     "PCI:0:2:0"
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
	DefaultDepth    16
	SubSection "Display"
		Depth 16
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
	#DefaultDepth    24
#	SubSection "Display"
#		Depth           1
#		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth           4
#		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth           8
#		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth           15
#		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth           16
#		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth           24
#		Modes           "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
#	EndSubSection


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
	Screen 0	"Screen1" 
	Screen 1	"Screen2" RightOf "Screen1"
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

