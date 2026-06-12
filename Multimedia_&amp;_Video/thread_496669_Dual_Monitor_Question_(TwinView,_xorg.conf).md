---
title: "Dual Monitor Question (TwinView, xorg.conf)"
date: 2007-07-09
forum: Multimedia &amp; Video
---

### Post by frantic211 on 2007-07-09
Hello,
I am sorry if this question has been answered here in another thread, but I have been at it for like 3 hours (at work) and am at my wits end.  

I am on a Dell Latitude D820 running 6.10.  Everything works, but I am trying to get my 'main' desktop to be the laptop screen.

I had this working, then updated nvidia-glx to 1.0-9746, this broke my system entirely, figured out that it was because the kernel modual was still 1.0-8776, and could not find the update for the kernel.  So I downgraded nvidia-glx and thing are working again, but not until after I messed with my xorg.conf.  I have tried all the backup xorg.conf files that I had, but none of them seemed to correct the problem.  I have tried messing with the "ConnectedMonitor", "UseDisplayDevice", and "TwinViewXineramaInfoOrder" to no avail.  

Like I said, this DID work before and it was one stupid setting that I just can't remember.  Anyway, any help would be great.  Attached below is the relevant section of my /etc/X11/xorg.conf file.

Thanks in Advance,
Matt
[PHP]
Section "Device"
	Identifier     "NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev" "true"
	Option		"RenderAccel" "true"
	Option		"AllowGLXWithComposite" "true"
	Option		"backingstore" "true"
	Option		"AddARGBGLXVisuals" "True"
	Option		"TripleBuffer" "true"

Option "TwinView" "1"
Option "TwinViewXineramaInfoOrder" "DFP, CRT"
Option "ConnectedMonitor" "DFP, CRT"
Option "TwinViewOrientation" "DFP LeftOf CRT"
Option "NoPowerConnectorCheck"
Option "UseEdidFreqs" "1"
Option "Metamodes" "DFP-0: 1680x1050, CRT-0: 1280x1024"
Option "SecondMonitorHorizSync" "31-82"
Option "SecondMonitorVertRefresh" "56-76"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
Option		"AddARGBGLXVisuals" "True"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection
[/PHP]

---

### Post by frantic211 on 2007-07-09
I also tried this, as suggested on a different forum:
[PHP]
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "UseFBDev" "true"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP, CRT"
    Option         "ConnectedMonitor" "DFP, CRT"
    Option         "UseDisplayDevice" "DFP, CRT"
    Option         "TwinViewOrientation" "DFP LeftOf CRT"
    Option         "NoPowerConnectorCheck"
    Option         "UseEdidFreqs" "1"
    Option         "Metamodes" "DFP-0: 1680x1050, CRT-0: 1280x1024"
    Option         "SecondMonitorHorizSync" "31-82"
    Option         "SecondMonitorVertRefresh" "56-76"
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

[/PHP]

But is still is the same result...
Thanks,
Matt

---

### Post by frantic211 on 2007-07-10
bump

---

### Post by sovietfunk on 2007-07-13
Have you tried configuring with "sudo dpkg-reconfigure -phigh xserver-xorg"? I've never done it that way, but it is the recommended method, i gather. You should also check your /var/log/Xorg.0.log and post it if you need help tracking the failure. 

I'll post my setup for reference, it works ok for me, except there's a powermanager (in KDE) that started crashing after i reinstated this setup recently. This happens even when the external monitor is not connected, and I'm not certain that it has anything to do with the dual monitor setup, but I think it does..  Another gripe is that my desktop icons get messed up - they stay on the laptop monitor's desktop, but never keep positions if i boot without the ext monitor and then with it again. 

My setup is for a laptop screen with a resolution of 1920x1280, with a dpi of 120 so that text doesn't get too tiny.  You'll have to change sync and modelines, the UseEdidDpi option and the DPI option to suit your screen.  The external monitor is a flatscreen with a resolution of 1280x1024. In server layout it is positioned "Above" the laptop screen, but this can be changed to LeftOf or RightOf. If my conf works for you, you can start putting in the advanced options from your previous config one by one and see that everything works ok.

And hey, I'm no guru, so if there's anything wonky or improvable about my setup I'd be happy for some tips back. 

```

Section "Files"
	# path to defoma fonts
    FontPath 	"/usr/share/X11/fonts/misc"
    FontPath 	"/usr/share/X11/fonts/100dpi:unscaled"
    FontPath 	"/usr/share/X11/fonts/75dpi:unscaled"
    FontPath 	"/usr/share/X11/fonts/Type1"
    FontPath 	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath 	"/usr/local/share/fonts"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
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
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA FX350M (internal)"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite"	"true"
	Option 		"MonitorLayout"		"LVDS, TMDS"
	Screen 		0
EndSection

Section "Device"
	Identifier	"NVIDIA FX350M (external)"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"MonitorLayout"		"LVDS, TMDS"
	Screen		1
EndSection

Section "Monitor"
    Identifier     "LCDPanel"
    VendorName     "Monitor Vendor"
    ModelName      "LCD Panel 1920x1200"
    HorizSync       31.5 - 90.0
    VertRefresh     60.0 - 60.0
    ModeLine       "1920x1200" 161.8 1920 2016 2048 2184 1200 1202 1208 1235 +hsync +vsync
    Option         "dpms"
    Option   "UseEdidDpi"   "FALSE"
    Option   "UseDisplayDevice" "DFP-0"
    Option   "DPI"   "120 x 120"
EndSection

Section "Monitor"
	Identifier	"External Monitor"
	Option		"DPMS"
	#HorizSync	30-64
	#HorizSync	15-94
	HorizSync	31.5-81
	#VertRefresh	50-76
	#VertRefresh	50-85
	VertRefresh	56-75
    Option         "dpms"
    Option   "UseEdidDpi"   "TRUE"
    Option   "UseDisplayDevice" "DFP-1"
    #Option   "DPI"   "120 x 120"
EndSection

Section "Extensions"
#	Option	"Composite"	"Enable"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA FX350M (internal)"
	Monitor		"LCDPanel"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier 	"External Screen"
	Device		"NVIDIA FX350M (external)"
	Monitor		"External Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1366x768" "1280x1024" "1024x768" "800x600" "640x480"
		# Modes	"1024x768" "800x600" "640x480"

	EndSubSection
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Default Screen"
	Screen	1	"External Screen" Above "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
#	Mode	0666
EndSection


```

---

