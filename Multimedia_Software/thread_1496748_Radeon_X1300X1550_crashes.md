---
title: "Radeon X1300/X1550 crashes"
date: 2010-05-29
forum: Multimedia Software
---

### Post by poppakap on 2010-05-29
I have been trying to get this Radeon PCI, 256mb (64 bit) card working for many months with no luck. I saw that Ubuntu 10.4 was out so I decided to take another crack at it. 

My machine is not a dinosaur, but not the latest either. I have a 650W power supply. 
My setup
PCCHips M963GV Mother board, 32 bit.
Intel Celeron 3.06ghz cpu
512 mb DDR ram
On board video connection that cannot be disabled
wireless nic card
80 gb hard drive
of course, DVD RW

I followed the instructions at [http://www.x.org/wiki/radeonBuildHowTo](http://www.x.org/wiki/radeonBuildHowTo) in order to download and build the latest open source driver. I managed to fight long enough to get an xorg.conf file generated, which my system does not like, and I was able to modify it as the instructions at that link specified, to load the correct drivers. Still no luck. 

I boot into a black screen. An S-video cable is attached to one of two televisions which never get a signal. Of course, I have to reboot again to stop the never ending black screen.

Can anyone see anything my log or xorg.conf that could indicate what my problem might be?

xorg.conf:
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
#	ModulePath   "/usr/lib/xorg/modules"
	ModulePath   "/opt/xorg/lib/xorg/modules,/usr/lib/xorg/modules"
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
	Load  "dbe"
	Load  "dri"
	Load  "record"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
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
	#DisplaySize	  310   230	# mm
	Identifier   "Monitor0"
	VendorName   "CPQ"
	ModelName    "COMPAQ FP745A"
	HorizSync    31.0 - 60.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "AccelMethod"        	# [<str>]
        #Option     "offscreensize"      	# [<str>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ignoreconnector"    	# [<str>]
        #Option     "forcereduced"       	# [<bool>]
        #Option     "forcedpi"           	# <i>
        #Option     "useconfiguredmonitor" 	# [<bool>]
        #Option     "HPD"                	# <str>
        #Option     "NoRandr"            	# [<bool>]
        #Option     "RROutputOrder"      	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "TVMode"             	# [<str>]
        #Option     "ScaleType"          	# [<str>]
        #Option     "UseAtomBIOS"        	# [<bool>]
        #Option     "AtomBIOS"           	# [<str>]
        #Option     "UnverifiedFeatures" 	# [<bool>]
        #Option     "Audio"              	# [<bool>]
        #Option     "AudioStreamSilence" 	# [<str>]
        #Option     "HDMI"               	# [<str>]
        #Option     "COHERENT"           	# [<str>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "LowPowerModeEngineClock" 	# <i>
	Identifier  "Card0"
	Driver      "radeonhd"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV505 CE [Radeon X1550 64-bit]"
	BusID       "PCI:2:0:0"
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
        #Option     "ForceCRT2Type"      	# <str>
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
        #Option     "ForceCRT1"          	# [<bool>]
        #Option     "XvOnCRT2"           	# [<bool>]
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
        #Option     "TVStandard"         	# <str>
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
        #Option     "CRT2Detection"      	# [<bool>]
        #Option     "ForceCRT2ReDetection" 	# [<bool>]
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
	Identifier  "Card1"
	Driver      "sis"
	VendorName  "Silicon Integrated Systems [SiS]"
	BoardName   "661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
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

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
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







X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux Ubuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=139cf981-460e-4a89-baf3-4a5441395481 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 29 17:02:06 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Card1"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/opt/xorg/lib/xorg/modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1039:6330:0000:0000 Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter rev 0, Mem @ 0xb0000000/134217728, 0xdfde0000/131072, I/O @ 0x0000cc00/128
(--) PCI: (0:2:0:0) 1002:715f:148c:2224 ATI Technologies Inc RV505 CE [Radeon X1550 64-bit] rev 0, Mem @ 0xc0000000/268435456, 0xdfe00000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
(--) PCI: (0:2:0:1) 1002:717f:148c:2225 ATI Technologies Inc rev 0, Mem @ 0xdfef0000/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "radeonhd"
(II) Loading /usr/lib/xorg/modules/drivers/radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.7.3.902, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
	RV505 : Radeon X1550, X1550 64bit.
	RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
	RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
	R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
	RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
	RV535 : Radeon X1300, X1650.
	RV550 : Radeon X2300 HD.
	RV560 : Radeon X1650.
	RV570 : Radeon X1950, X1950 GT; FireGL V7400.
	R580  : Radeon X1900, X1950; AMD Stream Processor.
	R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
	RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
	RV620 : Radeon HD 3450, HD 3470.
	RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
		FireGL V3600/V5600.
	RV635 : Radeon HD 3650, HD 3670.
	RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
	R680  : Radeon HD 3870 X2.
	M52   : Mobility Radeon X1300.
	M54   : Mobility Radeon X1400; M54-GL.
	M56   : Mobility Radeon X1600; Mobility FireGL V5200.
	M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
	M62   : Mobility Radeon X1350.
	M64   : Mobility Radeon X1450, X2300.
	M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
	M68   : Mobility Radeon X1900.
	M71   : Mobility Radeon HD 2300.
	M72   : Mobility Radeon HD 2400; Radeon E2400.
	M74   : Mobility Radeon HD 2400 XT.
	M76   : Mobility Radeon HD 2600;
		(Gemini ATI) Mobility Radeon HD 2600 XT.
	M82   : Mobility Radeon HD 3400.
	M86   : Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700.
	M88   : Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2.
	RS600 : Radeon Xpress 1200, Xpress 1250.
	RS690 : Radeon X1200, X1250, X1270.
	RS740 : RS740, RS740M.
	RS780 : Radeon HD 3100/3200/3300 Series.
	R700  : Radeon R700.
	RV710 : Radeon HD4570, HD4350.
	RV730 : Radeon HD4670, HD4650.
	RV740 : Radeon HD4770. EXPERIMENTAL AND UNTESTED.
	RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
	RV790 : Radeon HD 4890.
	M92   : Mobility Radeon HD4330, HD4530, HD4570. EXPERIMENTAL.
	M93   : Mobility Radeon M93. EXPERIMENTAL AND UNTESTED.
	M96   : Mobility Radeon HD4600.
	M97   : Mobility Radeon HD4860. EXPERIMENTAL AND UNTESTED.
	M98   : Mobility Radeon HD4850, HD4870.

(II) RADEONHD: version 1.3.0, built from dist of git branch master, commit 8cbff7bf

(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for sis
(--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
(==) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Selected EXA 2D acceleration.
(II) RADEONHD(0): Card not in database: 0x715F:0x148C:0x2224; using generic modesetting.
	If - and only if - your card does not work or does not work optimally
	please contact [email]radeonhd@opensuse.org[/email] to help rectify this.
	Use the subject: 0x715F:0x148C:0x2224: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an RV505 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xdfe00000 to 0xb7802000 (size 0x00010000)
(II) RADEONHD(0): PCIE Card Detected
(II) RADEONHD(0): Getting BIOS copy from PCI ROM
(II) RADEONHD(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x148c SubsystemID: 0x2224
	IOBaseAddress: 0x0000
	Filename: 69104DAA.HDA
	BIOS Bootup Message: 

 RV505CE DDR2 BIOS                                      

                    
(II) RADEONHD(0): Default Engine Clock: 350000
(II) RADEONHD(0): Default Memory Clock: 350000
(II) RADEONHD(0): Calling ASIC Init
(II) RADEONHD(0): ASIC_INIT Successful
(II) RADEONHD(0): Analog TV Default Mode: 136118949
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 0
(WW) RADEONHD(0): rhdAtomGetFbBaseAndSize: AtomBIOS specified VRAM scratch space size invalid
(II) RADEONHD(0):  default to: 20480
(II) RADEONHD(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEONHD(0): Default Engine Clock: 350000
(II) RADEONHD(0): Default Memory Clock: 350000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1100000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): Found libdri 5.4.0.
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:02:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
(II) RADEONHD(0): Found libdrm 1.3.0.
(II) RADEONHD(0): Found radeon drm 2.0.0.
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEONHD(0): Default Engine Clock: 350000
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1100000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00000000 (size = 0x00004000)
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00004000 (size = 0x00004000)
(II) RADEONHD(0): FirmwareInfo Revision 0103
(II) RADEONHD(0): Unused attribute: ul3DAccelerationEngineClock 0
(II) RADEONHD(0): Unused attribute: ulDriverTargetEngineClock 600000
(II) RADEONHD(0): Unused attribute: ulDriverTargetMemoryClock 600000
(II) RADEONHD(0): Unused attribute: ucASICMaxTemperature 0
(II) RADEONHD(0): Scary bits: Estimated MinEngineClock 250000 kHz
(II) RADEONHD(0): Scary bits: Estimated MinMemoryClock 250000 kHz
(II) RADEONHD(0): No VoltageObjectInfo table
(II) RADEONHD(0): Default Engine Clock: 350000
(II) RADEONHD(0): Default Memory Clock: 350000
(II) RADEONHD(0): Current Engine Clock: 344250
(II) RADEONHD(0): Current Memory Clock: 342000
(WW) RADEONHD(0): Unusupported SetVoltage Revision
(II) RADEONHD(0): Power Management: used engine clock / memory clock / core (VDDC) voltage   (0: ignore)
(II) RADEONHD(0): Power Management: Raw Ranges
(II) RADEONHD(0):   Minimum    250000 kHz /   250000 kHz /  0.000 V
(II) RADEONHD(0):   Maximum    350000 kHz /   400000 kHz /  0.000 V
(II) RADEONHD(0):   Default    350000 kHz /   350000 kHz /  0.000 V
(II) RADEONHD(0): PowerPlayInfo Revision 0000
(EE) RADEONHD(0): Unusupported PowerPlayInfo Revision
(II) RADEONHD(0): Query for Get Chip Configs: not implemented
(EE) RADEONHD(0): Power Management: Cannot get known good chip configurations
(II) RADEONHD(0): Power Management: Validated Ranges
(II) RADEONHD(0):   Minimum    250000 kHz /   250000 kHz /  0.000 V
(II) RADEONHD(0):   Maximum    350000 kHz /   400000 kHz /  0.000 V
(II) RADEONHD(0):   Default    350000 kHz /   350000 kHz /  0.000 V
(II) RADEONHD(0): Power Management: Final Levels
(II) RADEONHD(0):   Off        250000 kHz /   250000 kHz /  0.000 V
(II) RADEONHD(0):   Idle       350000 kHz /   350000 kHz /  0.000 V
(II) RADEONHD(0):   Slow2D     350000 kHz /   350000 kHz /  0.000 V
(II) RADEONHD(0):   Fast2D     350000 kHz /   350000 kHz /  0.000 V
(II) RADEONHD(0):   Slow3D     350000 kHz /   350000 kHz /  0.000 V
(II) RADEONHD(0):   Fast3D     350000 kHz /   350000 kHz /  0.000 V
(II) RADEONHD(0):   Max3D      350000 kHz /   400000 kHz /  0.000 V
(II) RADEONHD(0):   User       350000 kHz /   350000 kHz /  0.000 V
(EE) RADEONHD(0): rhdAtomGetDDCIndex: GPIO_DDC Index 13 exceeds maximum 5
(II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_VGA, "VGA CRT1", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_TV, "SVIDEO TV1", RHD_DDC_NONE, RHD_HPD_NONE, { RHD_OUTPUT_DACB, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[2] {RHD_CONNECTOR_DVI, "DVI-I DFP1", RHD_DDC_1, RHD_HPD_0, { RHD_OUTPUT_DACB, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[3] {RHD_CONNECTOR_VGA, "DVI-I CRT2", RHD_DDC_1, RHD_HPD_NONE, { RHD_OUTPUT_DACB, RHD_OUTPUT_NONE } }
(--) RADEONHD(0): Attaching Output DAC A to Connector VGA 1
(--) RADEONHD(0): Attaching Output DAC B to Connector TV SVIDEO
(--) RADEONHD(0): Attaching Output DAC B to Connector DVI-A 1
(--) RADEONHD(0): Attaching Output DAC B to Connector VGA 2
(II) RADEONHD(0): RandR: Adding RRoutput VGA_1 for Output DAC A
(II) RADEONHD(0): RandR: Adding RRoutput TV_SVIDEO for Output DAC B
(II) RADEONHD(0): RandR: Adding RRoutput DVI-A_1 for Output DAC B
(II) RADEONHD(0): RandR: Adding RRoutput VGA_2 for Output DAC B
(II) RADEONHD(0): Output VGA_1 using monitor section Monitor0
(II) RADEONHD(0): Output VGA_1 has no monitor section
(II) RADEONHD(0): Output TV_SVIDEO has no monitor section
(II) RADEONHD(0): Output DVI-A_1 has no monitor section
(II) RADEONHD(0): Output VGA_2 has no monitor section
(II) RADEONHD(0): EDID for output VGA_1
(II) RADEONHD(0): EDID for output TV_SVIDEO
(II) RADEONHD(0): EDID for output DVI-A_1
(II) RADEONHD(0): EDID for output VGA_2
(II) RADEONHD(0): Output VGA_1 disconnected
(II) RADEONHD(0): Output TV_SVIDEO disconnected
(II) RADEONHD(0): Output DVI-A_1 disconnected
(II) RADEONHD(0): Output VGA_2 disconnected
(WW) RADEONHD(0): No outputs definitely connected, trying again...
(II) RADEONHD(0): Output VGA_1 disconnected
(II) RADEONHD(0): Output TV_SVIDEO disconnected
(II) RADEONHD(0): Output DVI-A_1 disconnected
(II) RADEONHD(0): Output VGA_2 disconnected
(WW) RADEONHD(0): Unable to find initial modes
(EE) RADEONHD(0): RandR: No valid modes. Disabling RandR support.
(EE) RADEONHD(0): Failed to detect a connected monitor
(II) SIS(1): SiS driver (2005/09/20-1, compiled for X.org 1.7.6.0)
(II) SIS(1): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(1): *** See [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
(II) SIS(1): *** for documentation and updates.
(--) SIS(1): sisfb not found
(--) SIS(1): Relocated I/O registers at 0xCC00
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) SIS(1): Depth 24, (--) framebuffer bpp 32
(==) SIS(1): RGB weight 888
(==) SIS(1): Default visual is TrueColor
(WW) SIS(1): Could not find/read video BIOS
(==) SIS(1): Using XAA acceleration architecture
(==) SIS(1): Using HW cursor
(==) SIS(1): Color HW cursor is enabled
(II) SIS(1): Using VRAM command queue, size 512k
(==) SIS(1): Hotkey display switching is enabled
(II) SIS(1): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(1):          whether enabled or disabled. This is no driver bug.
(==) SIS(1): SiSCtrl utility interface is disabled
(II) SIS(1): For information on SiSCtrl, see
		[http://www.winischhofer.at/linuxsispart1.shtml#sisctrl](http://www.winischhofer.at/linuxsispart1.shtml#sisctrl)
(==) SIS(1): DRI disabled
(II) SIS(1): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(1): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(1): DIMM0 is DDR SDRAM
(--) SIS(1): DIMM1 is not installed
(--) SIS(1): DIMM2 is not installed
(--) SIS(1): DRAM type: DDR SDRAM
(--) SIS(1): Memory clock: 332.892 MHz
(--) SIS(1): DRAM bus width: 64 bit
(--) SIS(1): Linear framebuffer at 0xB0000000
(--) SIS(1): MMIO registers at 0xDFDE0000 (size 64K)
(--) SIS(1): VideoRAM: 32768 KB
(II) SIS(1): Using 32192K of framebuffer memory at offset 0K
(--) SIS(1): Hardware supports two video overlays
(==) SIS(1): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(1): Gamma correction is enabled
(II) SIS(1): Separate Xv gamma correction is disabled
(--) SIS(1): Memory bandwidth at 32 bpp is 665.784 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) SIS(1): CRT1 DDC supported
(--) SIS(1): CRT1 DDC level: 2 
(--) SIS(1): CRT1 DDC monitor info: *******************************************
(II) SIS(1): Manufacturer: CPQ  Model: 3059  Serial#: 1
(II) SIS(1): Year: 2001  Week: 43
(II) SIS(1): EDID Version: 1.3
(II) SIS(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) SIS(1): Sync:  Separate
(II) SIS(1): Max Image Size [cm]: horiz.: 31  vert.: 23
(II) SIS(1): Gamma: 2.20
(II) SIS(1): DPMS capabilities: Off; RGB/Color Display
(II) SIS(1): First detailed timing is preferred mode
(II) SIS(1): redX: 0.613 redY: 0.341   greenX: 0.288 greenY: 0.562
(II) SIS(1): blueX: 0.142 blueY: 0.115   whiteX: 0.305 whiteY: 0.324
(II) SIS(1): Supported established timings:
(II) SIS(1): 720x400@70Hz
(II) SIS(1): 640x480@60Hz
(II) SIS(1): 640x480@72Hz
(II) SIS(1): 640x480@75Hz
(II) SIS(1): 800x600@56Hz
(II) SIS(1): 800x600@60Hz
(II) SIS(1): 800x600@72Hz
(II) SIS(1): 800x600@75Hz
(II) SIS(1): 832x624@75Hz
(II) SIS(1): 1024x768@60Hz
(II) SIS(1): 1024x768@70Hz
(II) SIS(1): 1024x768@75Hz
(II) SIS(1): Manufacturer's mask: 0
(II) SIS(1): Supported standard timings:
(II) SIS(1): #0: hsize: 1024  vsize 768  refresh: 66  vid: 18017
(II) SIS(1): Supported detailed timing:
(II) SIS(1): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) SIS(1): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) SIS(1): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) SIS(1): Ranges: V min: 56 V max: 75 Hz, H min: 31 H max: 60 kHz, PixClock max 80 MHz
(II) SIS(1): Monitor name: COMPAQ FP745A
(II) SIS(1): Unknown vendor-specific block d
(II) SIS(1): EDID (in hex):
(II) SIS(1): 	08392f0985771d08a88e1f08d8d83009
(II) SIS(1): 	04000000e262e300348789bf40861f08
(II) SIS(1): 	f48f1e087b8789bf006d420000000000
(II) SIS(1): 	baf60b08f48f1e086b8789bf3c000000
(II) SIS(1): 	ef8689bffd193b00698789bf01000000
(II) SIS(1): 	ffffffff73c81d08f08689bf988789bf
(II) SIS(1): 	5ea80d08618789bf01000000ffffffff
(II) SIS(1): 	5bc81d08080000001f0000003c000000
(II) SIS(1): EDID vendor "CPQ", prod id 12377
(II) SIS(1): Using EDID range info for horizontal sync
(II) SIS(1): Using EDID range info for vertical refresh
(II) SIS(1): Printing DDC gathered Modelines:
(II) SIS(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) SIS(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) SIS(1): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) SIS(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) SIS(1): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) SIS(1): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) SIS(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) SIS(1): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) SIS(1): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) SIS(1): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) SIS(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) SIS(1): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) SIS(1): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
(--) SIS(1): According to DDC size, CRT1 aspect ratio is 1.35:1 (normal)
(--) SIS(1): End of CRT1 DDC monitor info *************************************
(==) SIS(1): Min pixel clock is 10 MHz
(--) SIS(1): Max pixel clock is 400 MHz
(II) SIS(1): Replaced default mode list with built-in modes
(II) SIS(1): Using fake widescreen modes for CRT1 VGA devices
(II) SIS(1): 	Use option "ForceCRT1VGAAspect" to overrule
(II) SIS(1): "Unknown reason" in the following list means that the mode
(II) SIS(1): is not supported on the chipset/bridge/current output device.
(II) SIS(1): Monitor1: Using hsync range of 31.00-60.00 kHz
(II) SIS(1): Monitor1: Using vrefresh range of 56.00-75.00 Hz
(II) SIS(1): Monitor1: Using maximum pixel clock of 80.00 MHz
(II) SIS(1): Estimated virtual size for aspect ratio 1.3478 is 1024x768
(II) SIS(1): Clock range:  10.00 to 400.00 MHz
(II) SIS(1): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(1): Not using default mode "800x600" (hsync out of range)
(II) SIS(1): Not using default mode "800x600" (hsync out of range)
(II) SIS(1): Not using default mode "800x600" (hsync out of range)
(II) SIS(1): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(1): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(1): Not using default mode "640x480" (hsync out of range)
(II) SIS(1): Not using default mode "640x480" (hsync out of range)
(II) SIS(1): Not using default mode "640x480" (hsync out of range)
(II) SIS(1): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(1): Not using default mode "1024x768" (hsync out of range)
(II) SIS(1): Not using default mode "1024x768" (hsync out of range)
(II) SIS(1): Not using default mode "1024x768" (hsync out of range)
(II) SIS(1): Not using default mode "1280x1024" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x1024" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x1024" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x1024" (width too large for virtual size)
(II) SIS(1): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(1): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(1): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(1): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(1): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(1): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(1): Not using default mode "1600x1200" (width too large for virtual size)
(II) SIS(1): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(1): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(1): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(1): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(1): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(1): Not using default mode "1920x1440" (width too large for virtual size)
(II) SIS(1): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(1): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(1): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(1): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(1): Not using default mode "2048x1536" (width too large for virtual size)
(II) SIS(1): Not using default mode "800x480" (vrefresh out of range)
(II) SIS(1): Not using default mode "1024x576" (hsync out of range)
(II) SIS(1): Not using default mode "1280x720" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x720" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x720" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x960" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x960" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x768" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x768" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x768" (width too large for virtual size)
(II) SIS(1): Not using default mode "1400x1050" (width too large for virtual size)
(II) SIS(1): Not using default mode "1400x1050" (width too large for virtual size)
(II) SIS(1): Not using default mode "1152x864" (width too large for virtual size)
(II) SIS(1): Not using default mode "1152x864" (width too large for virtual size)
(II) SIS(1): Not using default mode "1152x864" (width too large for virtual size)
(II) SIS(1): Not using default mode "848x480" (hsync out of range)
(II) SIS(1): Not using default mode "856x480" (hsync out of range)
(II) SIS(1): Not using default mode "1360x768" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x800" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x800" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x800" (width too large for virtual size)
(II) SIS(1): Not using default mode "1680x1050" (width too large for virtual size)
(II) SIS(1): Not using default mode "1920x1080" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x854" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x854" (width too large for virtual size)
(II) SIS(1): Not using default mode "1280x854" (width too large for virtual size)
(--) SIS(1): Virtual size is 1024x768 (pitch 1024)
(**) SIS(1): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) SIS(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) SIS(1): *Driver mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(1): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) SIS(1): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) SIS(1): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) SIS(1): *Driver mode "1024x768": 71.6 MHz, 52.7 kHz, 66.0 Hz
(II) SIS(1): Modeline "1024x768"x66.0   71.63  1024 1080 1192 1360  768 769 772 798 -hsync +vsync (52.7 kHz)
(**) SIS(1): *Default mode "1024x768": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(1): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) SIS(1): *Default mode "1024x768": 75.2 MHz, 56.6 kHz, 70.2 Hz
(II) SIS(1): Modeline "1024x768"x70.2   75.17  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.6 kHz)
(**) SIS(1): *Default mode "1024x768": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SIS(1): Modeline "1024x768"x60.1   65.15  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.5 kHz)
(**) SIS(1): *Default mode "1024x576": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(1): Modeline "1024x576"x75.0   78.75  1024 1040 1136 1312  576 686 690 800 +hsync +vsync (60.0 kHz)
(**) SIS(1): *Default mode "1024x576": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SIS(1): Modeline "1024x576"x60.1   65.15  1024 1048 1184 1344  576 688 694 806 +hsync +vsync (48.5 kHz)
(**) SIS(1): *Default mode "960x600": 41.5 MHz, 37.1 kHz, 60.0 Hz
(II) SIS(1): Modeline "960x600"x60.0   41.50  960 1008 1088 1120  600 603 609 618 +hsync +vsync (37.1 kHz)
(**) SIS(1): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) SIS(1): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) SIS(1): *Default mode "960x540": 37.3 MHz, 33.8 kHz, 60.0 Hz
(II) SIS(1): Modeline "960x540"x60.0   37.29  960 976 1008 1104  540 543 549 563 +hsync +vsync (33.8 kHz)
(**) SIS(1): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SIS(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) SIS(1): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) SIS(1): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) SIS(1): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(1): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SIS(1): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) SIS(1): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SIS(1): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SIS(1): Modeline "800x600"x75.0   49.52  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) SIS(1): *Default mode "800x600": 50.1 MHz, 48.2 kHz, 72.4 Hz
(II) SIS(1): Modeline "800x600"x72.4   50.11  800 856 976 1040  600 637 643 666 +hsync +vsync (48.2 kHz)
(**) SIS(1): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(1): Modeline "800x600"x60.3   39.97  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) SIS(1): *Default mode "800x600": 36.1 MHz, 35.2 kHz, 56.3 Hz
(II) SIS(1): Modeline "800x600"x56.3   36.06  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) SIS(1): *Default mode "768x576": 35.0 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(1): Modeline "768x576"x60.1   35.00  768 792 872 976  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(1): *Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(1): Modeline "720x576"x60.1   32.73  720 744 816 912  576 578 581 597 +hsync +vsync (35.9 kHz)
(**) SIS(1): *Default mode "856x480": 33.9 MHz, 31.7 kHz, 59.8 Hz
(II) SIS(1): Modeline "856x480"x59.8   33.94  856 872 1000 1072  480 492 495 529 -hsync -vsync (31.7 kHz)
(**) SIS(1): *Default mode "848x480": 33.7 MHz, 31.0 kHz, 60.0 Hz
(II) SIS(1): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 -hsync -vsync (31.0 kHz)
(**) SIS(1): *Default mode "800x480": 49.5 MHz, 46.9 kHz, 75.1 Hz
(II) SIS(1): Modeline "800x480"x75.1   49.52  800 816 896 1056  480 551 554 624 +hsync +vsync (46.9 kHz)
(**) SIS(1): *Default mode "800x480": 39.8 MHz, 37.7 kHz, 60.0 Hz
(II) SIS(1): Modeline "800x480"x60.0   39.77  800 840 968 1056  480 552 556 628 +hsync +vsync (37.7 kHz)
(**) SIS(1): *Default mode "720x480": 28.3 MHz, 31.6 kHz, 61.0 Hz
(II) SIS(1): Modeline "720x480"x61.0   28.28  720 728 840 896  480 490 492 517 -hsync -vsync (31.6 kHz)
(**) SIS(1): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SIS(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) SIS(1): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SIS(1): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) SIS(1): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) SIS(1): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) SIS(1): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SIS(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) SIS(1): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SIS(1): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) SIS(1): *Default mode "640x480": 25.1 MHz, 31.3 kHz, 59.7 Hz
(II) SIS(1): Modeline "640x480"x59.7   25.06  640 656 752 800  480 490 492 525 -hsync -vsync (31.3 kHz)
(**) SIS(1): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) SIS(1): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) SIS(1): *Default mode "640x400": 25.1 MHz, 31.6 kHz, 71.6 Hz
(II) SIS(1): Modeline "640x400"x71.6   25.06  640 656 752 792  400 413 415 442 -hsync +vsync (31.6 kHz)
(**) SIS(1): *Default mode "512x384": 32.6 MHz, 48.5 kHz, 60.1 Hz (D)
(II) SIS(1): Modeline "512x384"x60.1   32.57  512 528 592 672  384 385 388 403 doublescan -hsync -vsync (48.5 kHz)
(**) SIS(1): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SIS(1): Modeline "400x300"x60.3   19.98  400 416 480 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) SIS(1): *Default mode "320x240": 12.5 MHz, 31.3 kHz, 60.7 Hz (D)
(II) SIS(1): Modeline "320x240"x60.7   12.53  320 328 376 400  240 245 246 258 doublescan -hsync -vsync (31.3 kHz)
(**) SIS(1): *Default mode "320x200": 12.5 MHz, 31.3 kHz, 70.9 Hz (D)
(II) SIS(1): Modeline "320x200"x70.9   12.53  320 328 376 400  200 206 207 221 doublescan -hsync +vsync (31.3 kHz)
(**) SIS(1): Display dimensions: (310, 230) mm
(**) SIS(1): DPI set to (83, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) SIS(1): 2D acceleration enabled

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x2d0410]
3: /usr/bin/X (InitOutput+0xcac) [0x80ba36c]
4: /usr/bin/X (0x8048000+0x1ebbb) [0x8066bbb]
5: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x2e7bd6]
6: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address 0x18

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by Rrogers on 2010-05-30
Hopefully somebody with _real_ expertise will answer but...
Feel free to completely ignore the following.

Does your system work (do anything useful) with a live DVD?  In particular the 9.10 version.  In other words why are you compiling your own X system? To bring the card up?
Does it do anything with no xorg.conf?  
Assuming that you get one moniter working that way; I would try to remove items from the xorg.conf file.  Starting from the bottom.  I would also go through and remove, or fix, all the things that were complained about in the log file.
In 9.10 I have a minimalistic xorg.conf file.  Just sufficient to overcome things that went wrong and provide a second monitor.

In my xorg.conf module section I only have 
Section "Module"
    Load "glx"
    Load "dri"
EndSection  

  Your extra modules apparently are invoking the 2D EXA; which is suspicious since the 2D immediately precedes the segmentation fault.    Now that I look at my log file; it is gripping about dri but whatever recovery it did worked.  I think, the next time I want to waste a day, I will kill the "dri" and find a replacement it likes.





I had a similar problem with onboard and card Video interfaces.  Fortunately I was able to select the card in the BIOS setup.  Even with that Lucid failed, and I stuck with Karmac rather than try to force it through.  I did report the failure.  As far as I could tell the KMS settings are a problem and should be killed off; although I forget how.

---

### Post by poppakap on 2010-05-30
Ignore you? Are you kidding? I need all the help I can get! And you're the only one to offer anything yet, so I will try exactly as you have suggested.

I had wondered if perhaps a 64 bit video card might be incompatible with a 32 bit OS or if that referred to different "bits."

Actually, without an xorg.conf, my on board video works perfectly with my lcd monitor. I read that the xorg.conf is deprecated and only for using a custom driver. So I actually got the source for the open-source driver and compiled it and followed those instructions to try to get it to load the driver from /opt/xorg/blah blah/xorg/modules... Anyway, everything works but the high dollar (so to speak) radeon card. And if I throw that xorg.conf that I have listed into the /etc/X11 directory it just won't show anything when x windows starts.

Anyway, I am going to give your suggestions a shot later on today after I finish killing myself in my hot, humid yard today!

Thank you so much! I will let you know what happens with this.

---

### Post by Rrogers on 2010-05-30
In that case I can put my xorg.conf up on google.  It's elementary.  You would have to change monitor1 to fit your system.  
Looking at my xorg.conf I am not sure it will help since I have a dual headed card.  It does show some things that didn't work; commented out.
I also have a couple of multiscreen utilites that might help if you run without xorg.conf.  They are standard and helped but I don't rememer when:)
ARandR
Multiple Screens

I think they help with sizing and placing; to get info for xorg.conf.
You have to forgive my vagueness I am getting older and can't keep all of these software "Wabes" (as in the Jaberwock) straight any longer.  
If you want I can find the Ubuntu package names.

Ray

---

