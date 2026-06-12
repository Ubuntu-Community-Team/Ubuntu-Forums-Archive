---
title: "Ubuntu 7.10 - ATI fglrx - Big Desktop -- Resolution Issues - Please help"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by ScoobyInc on 2008-01-20
Hello;

This is my first post, but long time reader. I had a perfect working dual monitor setup on Ubuntu 7.04, and cannot get a working setup with Ubuntu 7.10.

I read multiple (if not all that I can find) posts regarding this, I tried multiple methods, I spent over 50+ working hours trying to get this to work. I absolutely cannot arrive at a perfect solution.

What I have:

OS == Ubuntu 7.10
CARD == ATI Radeon X600
DRIVER == fglrx 8.44.3
MONITOR 1 == Dell 2005FPW (Running 1680x1050)
MONITOR 2 == Dell E172FP (Running 1024x768, should be 1280x1024)

I am running big desktop, with a resolution of 2960x1050. The main display is running at 1680x1050 perfectly. The second monitor is only running at 1024x768 when it should be 1280x1024. I cannot get the second monitor to show the correct resolution after multiple attempts. 

Does anyone have any ideas or suggestions??

related sections ofxorg.conf:
```

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	HorizSync    31.4 - 80.0
	VertRefresh  56.0 - 75.0
	ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
	ModeLine     "1280x1024" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

	#Option	    "VideoOverlay" "on"
	#Option	    "OpenGLOverlay" "off"
	#Option	    "DesktopSetup" "horizontal"
	#Option	    "PairModes" "1680x1050+1280x1024"
	#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "Capabilities" "0x00000800"
	#Option	    "PairMode" "1680x1050+1280x1024"
	Option	    "MergedFB" "true" #Enable MergedFB function
	Option	    "MonitorLayout" "TMDS,CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
	Option	    "ForceMonitors" "tmds1,crt1"
	Option	    "CRT2Hsync" "31-80" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option	    "CRT2VRefresh" "56-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	Option	    "OverlayOnCRTC2" "true"
	Option	    "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
	Option	    "MetaModes" "1680x1050-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
	Option	    "PairModes" "1680x1050+1280x1024"
	Option      "MergedNonRectangular" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"

#		Viewport   0 0
#		Virtual   1280 1024
		Depth     24
		Modes    "1680x1050" "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```


Screenshots:
[IMG]http://img174.imageshack.us/img174/6750/resolution01.jpg[/IMG]

[IMG]http://img174.imageshack.us/img174/9884/screens01.jpg[/IMG]

[IMG]http://img174.imageshack.us/img174/2788/ati01.jpg[/IMG]

[IMG]http://img174.imageshack.us/img174/2788/ati02.jpg[/IMG]

[IMG]http://img174.imageshack.us/img174/2788/ati03.jpg[/IMG]

[IMG]http://img174.imageshack.us/img174/2788/ati04.jpg[/IMG]


Any help I would greatly appreciate it! Thanks in advance!

---

### Post by hangfire on 2008-01-20
Buy nVidia.

Seriously.

-HF

---

### Post by Resonance378 on 2008-01-23
Is your issue anything like this?
[http://wiki.cchtml.com/index.php/Troubleshooting#BigDesktop_.28Dual_screen.29_doesn.27t_work_after_GDM_login_screen](http://wiki.cchtml.com/index.php/Troubleshooting#BigDesktop_.28Dual_screen.29_doesn.27t_work_after_GDM_login_screen)

---

### Post by ScoobyInc on 2008-01-27
> **Resonance378 said:**
> Is your issue anything like this?
[http://wiki.cchtml.com/index.php/Troubleshooting#BigDesktop_.28Dual_screen.29_doesn.27t_work_after_GDM_login_screen](http://wiki.cchtml.com/index.php/Troubleshooting#BigDesktop_.28Dual_screen.29_doesn.27t_work_after_GDM_login_screen)

Doesn't seem like it. The issue is visible at both the login screen and while using the machine (logged in).

Also my ```
Option  "DesktopSetup"
``` is already commented out (##)

---

