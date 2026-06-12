---
title: "2 videocards, 2 monitors, xinerama, crash, help!"
date: 2008-10-30
forum: Multimedia Software
---

### Post by Farenji on 2008-10-30
I'm trying to get a dual head setup working on ubuntu 8.04.1 but so far without success.

The computer is a Dell Optiplex 320. This is a problematic machine for linux, see google, I need to install GRUB2 cause GRUB1 doesn't boot, and I have to add the kernel params "pci=nomsi acpi=off" to get the machine to even boot (also needed to boot the live cd). 

The machine has a Ati Radeon on board, and I have a Nvidia 5200 (PCI) as secundary card. Both cards work fine - they are auto detected fine using "X -configure" and X boots normally - but the 2 screens are separate, only the mouse cursor is shared between the 2 screens, I can't move windows from one screen to the other, I just have 2 separate desktops. That's normal cause I need Xinerama to get one integrated desktop.

But when I enable Xinerama in xorg.conf (by adding 'Option "Xinerama" "on"' to the ServerLayout part) the machine grinds to a halt and the screen flickers a bit and then stays blank. Only a hard reboot helps after that, ctrl-alt-backspace or ctrl-alt-del have no effect.

I have been experimenting for a week now, without success. I tried other video drivers (ati, radeon, fglrx, vesa, even fbdev), I tried different video cards (another PCI Ati Radeon instead of the nvidia), I have disabled all non-essential modules but the problem stays the same.

On windows xp everything works fine, including dual head with one big desktop.

The Xorg.log doesn't give me any clues. I get a few warnings:

> 
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(WW) RADEON(0): Failed to set up write-combining range (0xb0000000,0x2000000)
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
(WW) RADEON(0): Direct rendering disabled
(WW) NV(1): Failed to set up write-combining range (0xc0000000,0x10000000)


But no errors. Here's my xorg.conf:

> 
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option	"Xinerama" "on"

EndSection




Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "glx"
	Load  "xtrap"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "GLcore"
	Load  "dbe"
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
	#DisplaySize	  340   270	# mm
	Identifier   "Monitor0"
	VendorName   "DEL"
	ModelName    "DELL E177FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    31.0 - 80.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	#DisplaySize	  340   270	# mm
	Identifier   "Monitor1"
	VendorName   "DEL"
	ModelName    "DELL E177FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    31.0 - 80.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "DDCMode"            	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "DynamicClocks"      	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
	Identifier  "Card0"
	# Driver      "ati"
	Driver      "fbdev"
	VendorName  "ATI Technologies Inc"
	BoardName   "RC410 [Radeon Xpress 200]"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card1"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV34 [GeForce FX 5200]"
	BusID       "PCI:2:2:0"
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




---

### Post by Farenji on 2008-10-30
I will try 8.10, I see it has a much newer kernel so it just might fix my issues, I'll keep you posted.

---

### Post by Farenji on 2008-11-01
Oh well. I discovered that the nvidia was a dual head card (I thought only cloned display was possible with the FX5200), so I got myself an adapter from vga to dvi, disabled the onboard ati card, installed the nvidia driver and nvidia-settings, and using the gui I had my dual monitor setup working in a few minutes. Yay! :)

Apparently it's totally impossible to create a dual monitor setup using an onboard ati and another pci card, but is it the 2 different graphic adapters or the dell optiplex 320 that's causing the troubles? Probably the latter. That was a week wasted, thanks dell.

---

