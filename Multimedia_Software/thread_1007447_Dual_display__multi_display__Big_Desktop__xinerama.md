---
title: "Dual display / multi display / Big Desktop / xinerama problems"
date: 2008-12-10
forum: Multimedia Software
---

### Post by SamTzu on 2008-12-10
Always the same old song and dance.
I'm at the point of moving back to M$ products and/or bying Nvidia card.

Here is my xorg.conf for those who have been fighting a losing battle with ATI X1?00 and dual display / multi display / Big Desktop / xinerama problems.
No wonder we are so lost when we can't even talk about it using same terminology.

Don't ask me why the X wants 3 Monitors when all I have is 2.



Sam



xorg.conf
-----------------------------------------------------------------------------------------------
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor 0"
EndSection

Section "Monitor"
    Identifier   "Configured Monitor 1"
    Option        "RightOf" "Configured Monitor 0"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "Configured Video Device"
    Monitor    "Configured Monitor 0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by iponeverything on 2008-12-10
Just tried dual head on mine. Very surprised!

8.10 (default xorg -- ie auto detect everything) Xorg GPL ATI drivers.
ATI Technologies Inc Radeon Mobility M6 LY


Hooked up a sony 17" wide screen.

went to "system->preferences->screen resolution" and lo and behold -- there it was. It even let me set the correct crazy wide screen resolution.

---

### Post by CHaoSlayeR on 2008-12-10
You are not actually configuring a "BigDesktop" mode in your xorg.conf. You are just configuring two desktops and one of them stretched over two monitors:
```

Section "Monitor"
  Identifier "Configured Monitor 0"
EndSection

Section "Monitor"
  Identifier "Configured Monitor 1"
  Option "RightOf" "Configured Monitor 0"
EndSection

```

That's why it wants three displays.

I would also suggest you first give iponeverything's approach a try. When that doesn't work use the AMD/ATI Catalyst Control Center. But before that you may have to reset your xorg.conf to a valid basic configuration to be started on by the CCC.

This can be done with the following command:
```

aticonfig --initial=dual-head --screen-layout=left

```

That should create a basic BigDesktop configuration that **should** work. If it doesn't come back here. I've recently struggled again a lot with the fglrx driver.

I am using two CRTs for my configuration but that shouldn't make a difference. Here are the relevant parts of my xorg.conf for reference:
```

Section "Monitor"
#	Option	    "VendorName" "Sampo"
#	Option	    "ModelName" "AlphaScan 871"
	Identifier   "Monitor0"
	HorizSync    27.0 - 100.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
#	Option	    "VendorName" "Iiyama"
#	Option	    "ModelName" "Vision Master 450"
	Identifier   "Monitor1"
	HorizSync    27.0 - 102.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
#	Option	    "AccelMethod" 		"EXA"
#	Option	    "AddARGBGLXVisuals" 	"true"
#	Option	    "AllowGLXWithComposite" 	"true"
#	Option	    "Mode2" 			"1280x1024" #Resolution for second monitor
#	Option	    "mtrr" 			"no" # disable DRI mtrr mapper, driver has its own code for mtrr!
#	Option	    "no_accel" 			"no"
#	Option	    "no_dri" 			"no"
#	Option	    "XaaNoOffscreenPixmaps" 	"true" # unsupported as of 8.10
#	Option	    "BlockSignalsOnLock" "on"
#	Option	    "DRI" "true"
#	Option	    "ForceGenericCPU" "off"
#	Option	    "KernelModuleParm" "locked-userpages=0"
#	Option	    "MigrationHeuristic" 	"greedy"
#	Option	    "RenderAccel" "true" # unsupported as of 8.10
	Identifier  "Device0"
	Driver      "fglrx"
	BoardName   "ATI Radeon HD2400 Pro"
	Option	    "BackingStore" "on"
#	Option	    "EnablePrivateBackZ" 	"yes" #Enable 3d support <= May Not Work
	Option	    "UseFastTLS" "1" # 0 -> Fast, 1 -> Faster, 2 -> Compatible (WINE)
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedVideo" "on"
	Option	    "TexturedVideoSync" "on"
	Option	    "VideoOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
#	Option	    "DPMS"
	Option	    "EnableMonitor" "crt1,crt2"
#	Option	    "EnablePageFlip" 		"true"
	Option	    "HSync2" "27.0 - 102.0" #This sets the horizontal sync for the secondary display.
	Option	    "PairModes" "1280x1024+1280x1024"
	Option	    "Textured2D" "on"
	Option	    "VRefresh2" "50.0 - 160.0" #This sets the refresh rate of the secondary display.
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Device0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

---

