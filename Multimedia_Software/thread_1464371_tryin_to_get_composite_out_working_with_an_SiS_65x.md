---
title: "tryin to get composite out working with an SiS 65x/M750/740"
date: 2010-04-28
forum: Multimedia Software
---

### Post by aeltester on 2010-04-28
mornin experts,

I am trying to enable the Composite out of the integrated graphics card as default and thus permanently. However, I have not even succeeded at getting it to work AT ALL. Using karmic, I had to create a fresh xorg.conf which seems to be looked at since the system doesn't start if I mess around in it. I dug through google and the man pages of the driver for hours but don't see where I went wrong.
thanks in advance.

This is what it looks like:

```
paprika@paprika-htpc:/etc/X11$ cat xorg.conf
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "extmod"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "record"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "Accel"              	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "TurboQueue"         	# [<bool>]
        #Option     "FastVram"           	# [<bool>]
        #Option     "HostBus"            	# [<bool>]
        #Option     "RenderAcceleration" 	# [<bool>]
        #Option     "ForceCRT1Type"      	# <str>
        Option     "ForceCRT2Type" "COMPOSITE" 	# <str>
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "Vesa"               	# [<bool>]
        #Option     "MaxXFBMem"          	# <i>
        #Option     "EnableSiSCtrl"      	# [<bool>]
        #Option     "SWCursor"           	# [<bool>]
        #Option     "HWCursor"           	# [<bool>]
        #Option     "UseColorHWCursor"   	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "Reflect"            	# <str>
        #Option     "Xvideo"             	# [<bool>]
        #Option     "InternalModes"      	# [<bool>]
        #Option     "OverruleFrequencyRanges" 	# [<bool>]
        #Option     "RestoreBySetMode"   	# [<bool>]
        #Option     "ForceCRT1"           	# [<bool>]
        Option     "XvOnCRT2" "True"           	# [<bool>]
        #Option     "PanelDelayCompensation" 	# <i>
        #Option     "PDC"                	# <i>
        #Option     "PanelDelayCompensation2" 	# <i>
        #Option     "PDC2"               	# <i>
        #Option     "PanelDelayCompensation1" 	# <i>
        #Option     "PDC1"               	# <i>
        #Option     "EMI"                	# <i>
        #Option     "LVDSHL"             	# <i>
        #Option     "ForcePanelRGB"      	# <i>
        #Option     "SpecialTiming"      	# <str>
        Option     "TVStandard" "PAL"        	# <str>
        #Option     "UseROMData"         	# [<bool>]
        #Option     "UseOEMData"         	# [<bool>]
        #Option     "YV12"               	# [<bool>]
        #Option     "CHTVType"           	# [<bool>]
        #Option     "CHTVOverscan"       	# [<bool>]
        #Option     "CHTVSuperOverscan"  	# [<bool>]
        #Option     "CHTVLumaBandwidthCVBS" 	# <i>
        #Option     "CHTVLumaBandwidthSVIDEO" 	# <i>
        #Option     "CHTVLumaFlickerFilter" 	# <i>
        #Option     "CHTVChromaBandwidth" 	# <i>
        #Option     "CHTVChromaFlickerFilter" 	# <i>
        #Option     "CHTVCVBSColor"      	# [<bool>]
        #Option     "CHTVTextEnhance"    	# <i>
        #Option     "CHTVContrast"       	# <i>
        #Option     "SISTVEdgeEnhance"   	# <i>
        #Option     "SISTVAntiFlicker"   	# <str>
        #Option     "SISTVSaturation"    	# <i>
        #Option     "SISTVCFilter"       	# [<bool>]
        #Option     "SISTVYFilter"       	# <i>
        #Option     "SISTVColorCalibFine" 	# <i>
        #Option     "SISTVColorCalibCoarse" 	# <i>
        #Option     "SISTVXScale"        	# <i>
        #Option     "SISTVYScale"        	# <i>
        #Option     "TVXPosOffset"       	# <i>
        #Option     "TVYPosOffset"       	# <i>
        #Option     "SIS6326TVAntiFlicker" 	# <str>
        #Option     "SIS6326TVEnableYFilter" 	# [<bool>]
        #Option     "SIS6326TVYFilterStrong" 	# [<bool>]
        #Option     "SIS6326TVForcePlug" 	# <str>
        #Option     "SIS6326FSCAdjust"   	# <i>
        #Option     "YPbPrAspectRatio"   	# <str>
        #Option     "TVBlueWorkAround"   	# [<bool>]
        #Option     "ColorHWCursorBlending" 	# [<bool>]
        #Option     "ColorHWCursorBlendThreshold" 	# <i>
        Option     "CRT2Detection" "True"      	# [<bool>]
        Option     "ForceCRT2ReDetection" "True"# [<bool>]
        #Option     "SenseYPbPr"         	# [<bool>]
        #Option     "CRT1Gamma"          	# [<bool>]
        #Option     "CRT2Gamma"          	# [<str>]
        #Option     "GammaBrightness"    	# <str>
        #Option     "GammaBrightnessCRT2" 	# <str>
        #Option     "CRT2GammaBrightness" 	# <str>
        #Option     "Brightness"         	# <str>
        #Option     "NewGammaBrightness" 	# <str>
        #Option     "CRT2Brightness"     	# <str>
        #Option     "CRT2NewGammaBrightness" 	# <str>
        #Option     "Contrast"           	# <str>
        #Option     "NewGammaContrast"   	# <str>
        #Option     "CRT2Contrast"       	# <str>
        #Option     "CRT2NewGammaContrast" 	# <str>
        #Option     "CRT1Saturation"     	# <i>
        #Option     "XvGamma"            	# [<str>]
        #Option     "XvDefaultContrast"  	# <i>
        #Option     "XvDefaultBrightness" 	# <i>
        #Option     "XvDefaultHue"       	# <i>
        #Option     "XvDefaultSaturation" 	# <i>
        #Option     "XvDefaultDisableGfx" 	# [<bool>]
        #Option     "XvDefaultDisableGfxLR" 	# [<bool>]
        #Option     "XvChromaMin"        	# <i>
        #Option     "XvChromaMax"        	# <i>
        #Option     "XvUseChromaKey"     	# [<bool>]
        #Option     "XvInsideChromaKey"  	# [<bool>]
        #Option     "XvYUVChromaKey"     	# [<bool>]
        #Option     "XvDisableColorKey"  	# [<bool>]
        #Option     "XvUseMemcpy"        	# [<bool>]
        #Option     "BenchmarkMemcpy"    	# [<bool>]
        #Option     "UseSSE"             	# [<bool>]
        #Option     "XvDefaultAdaptor"   	# <str>
        #Option     "ScaleLCD"           	# [<bool>]
        #Option     "CenterLCD"          	# [<bool>]
        #Option     "EnableHotkey"       	# [<bool>]
        #Option     "ForceCRT1VGAAspect" 	# <str>
        #Option     "ForceCRT2VGAAspect" 	# <str>
        #Option     "MergedFB"           	# [<str>]
        #Option     "TwinView"           	# [<str>]
        #Option     "MergedFBAuto"       	# [<bool>]
        #Option     "CRT2HSync"          	# <str>
        #Option     "SecondMonitorHorizSync" 	# <str>
        #Option     "CRT2VRefresh"       	# <str>
        #Option     "SecondMonitorVertRefresh" 	# <str>
        #Option     "CRT2Position"       	# <str>
        #Option     "TwinViewOrientation" 	# <str>
        #Option     "MetaModes"          	# <str>
        #Option     "MergedDPI"          	# <str>
        #Option     "MergedXinerama"     	# [<bool>]
        #Option     "TwinviewXineramaInfo" 	# [<bool>]
        #Option     "MergedXineramaCRT2IsScreen0" 	# [<bool>]
        #Option     "MergedNonRectangular" 	# [<bool>]
        #Option     "MergedMouseRestriction" 	# [<bool>]
	Identifier  "Card0"
	Driver      "sis"
	VendorName  "Silicon Integrated Systems [SiS]"
	BoardName   "65x/M650/740 PCI/AGP VGA Display Adapter"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by prshah on 2010-04-28
> **aeltester said:**
> 
I am trying to enable the Composite out of the integrated graphics card as default and thus permanently.

Hi, please see my thread on this topic (with SiS card): [Re: Use only TV instead of monitor]("http://ubuntuforums.org/showpost.php?p=4446540&postcount=5")

Note that while this post is outdated, it will still work; there is probably an easier way using the xrandr command, but I've no more access to SiS and thus cannot test or recommend.

---

### Post by aeltester on 2010-04-28
thanks, after some searching I was able to find sisctrl and install it. After some fiddling with the option "EnableSisCtrl" "yes", I now get white lines flying around on the TV-screen and during boot, I even get some lines that look like the colors are being tested. In SisCtrl, I have no options under CRT1 or under CRT2, cannot switch any outputs or anything. I thought it had something to do with the free driver limiting the options I get in SisCtrl so I commented out any option in xorg.conf that I messed around with, returning it to the xorg -configure state. Some rebooting and I still don't get any options in SisCtrl. What might be the problem now?

thanks

---

### Post by prshah on 2010-04-28
> **aeltester said:**
> After some fiddling with the option "EnableSisCtrl" "yes", 

I'm sorry, the link seems to have changed; instead of the section on sisctrl, see section 5; or just ignore the link altogether and read the rest of the post for the changes to be made to your xorg.conf file.

I did not use (or understand) the sisctrl utility.

---

### Post by aeltester on 2010-04-29
I threw in a radeon 9200 pro (rv280) which I managed to get up and running. actually, I just needed to reboot and it worked. old onboad cheapass hw sucks.
still not solved.

---

