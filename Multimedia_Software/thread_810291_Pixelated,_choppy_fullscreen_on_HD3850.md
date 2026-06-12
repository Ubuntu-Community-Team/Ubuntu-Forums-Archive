---
title: "Pixelated, choppy fullscreen on HD3850"
date: 2008-05-28
forum: Multimedia Software
---

### Post by HydroDiOxide on 2008-05-28
Hi. I've got some really poor video playback on my Ati hd3850. Fullscreen is pixelated and choppy and I can't seem to find a sollution. I'm using the X11 output module in VLC and compiz-fusion as WM.

Here's my xorg.conf
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option	"AIGLX" "on"
EndSection

Section "Files"
	RgbPath      "/usr/share/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/misc"
	FontPath     "/usr/share/fonts/100dpi:unscaled"
	FontPath     "/usr/share/fonts/75dpi:unscaled"
	FontPath     "/usr/share/fonts/TTF"
	FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
	Load "type1"
	Load  "glx"	
	SubSection  "extmod"
		Option	"omit xfree86-dga"
	EndSubSection
	# Load  "xtrap"
	# Load  "record"
	# Load  "GLcore"
	Load  "dbe"
	Load  "dri"
	Load  "freetype"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option "XkbLayout" "us"
        Option "XkbVariant" "intl"
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
        #Option     "NoAccel"            	# [<bool>]
        #Option     "NoDRI"              	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "DRM_nbufs"          	# <i>
        #Option     "DRM_bufsize"        	# <i>
        #Option     "Capabilities"       	# <i>
        #Option     "CapabilitiesEx"     	# <i>
        #Option     "ClientDriverName"   	# [<str>]
        #Option     "KernelModuleParm"   	# [<str>]
        #Option     "AGPMask"            	# <i>
        #Option     "AGPv3Mask"          	# <i>
        #Option     "BufferTiling"       	# [<bool>]
        #Option     "Profile"            	# <str>
        #Option     "RingSize"           	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "GammaCorrectionI"   	# <i>
        #Option     "GammaCorrectionII"  	# <i>
        #Option     "OpenGLOverlay"      	"true"
        #Option     "DefaultVisualTrueColor" 	# [<bool>]
        Option     "VideoOverlay"       	"on"
        #Option     "DesktopSetup"       	# [<str>]
        #Option     "MonitorLayout"      	# [<str>]
        #Option     "ForceMonitors"      	# [<str>]
        #Option     "EnableMonitor"      	# <str>
        #Option     "OverlayOnCRTC2"     	# [<bool>]
        #Option     "Mode2"              	# [<str>]
        #Option     "PairModes"          	# [<str>]
        #Option     "HSync2"             	# [<str>]
        #Option     "VRefresh2"          	# [<str>]
        #Option     "ScreenOverlap"      	# <i>
        #Option     "MemClock"           	# <i>
        #Option     "ASICClock"          	# <i>
        #Option     "UseInternalAGPGART" 	# [<bool>]
        #Option     "FastSwap"           	# [<bool>]
        #Option     "Stereo"             	# [<bool>]
        #Option     "StereoSyncEnable"   	# <i>
        #Option     "DisableOvScaler"    	# [<bool>]
        #Option     "UseFastTLS"         	# <i>
        #Option     "BlockSignalsOnLock" 	# [<bool>]
        #Option     "ForceGenericCPU"    	# [<bool>]
        #Option     "CenterMode"         	# [<bool>]
        #Option     "OffScreenPixmaps"   	# [<bool>]
        #Option     "EnableOpaqueOverlayVisual" # [<bool>]
        #Option     "TMDSCoherentMode"   	# [<bool>]
        #Option     "EnablePrivateBackZ" 	# [<bool>]
        #Option     "TVFormat"           	# [<str>]
        #Option     "TVStandard"         	# [<str>]
        #Option     "TVOverscan"         	# [<bool>]
        #Option     "TVHSizeAdj"         	# <i>
        #Option     "TVVSizeAdj"         	# <i>
        #Option     "TVHPosAdj"          	# <i>
        #Option     "TVVPosAdj"          	# <i>
        #Option     "TVHStartAdj"        	# <i>
        #Option     "TVColorAdj"         	# <i>
        #Option     "PseudoColorVisuals" 	# [<bool>]
        #Option     "PreferredVRefresh"  	# <i>
        #Option     "FastStart"          	# [<bool>]
        #Option     "ProfileDriver"      	# [<bool>]
        #Option     "PPPTforGART"        	# [<bool>]
        Option     "TexturedVideo"      	"off"
        #Option     "TexturedVideoSync"  	#"true"
        #Option     "Textured2D"         	#"true"
        #Option     "TexturedXrender"    	"true"
        Option     "DPMS"               	"true"
        #Option     "MaxGARTSize"        	# <i>
        #Option     "LogoPosX"           	# <i>
        #Option     "LogoPosY"           	# <i>
        #Option     "LogoColFG"          	# <i>
        #Option     "LogoColBG"          	# <i>
        #Option     "SwapScreens"        	# [<bool>]
        #Option     "FBC"                	# [<bool>]
        #Option     "FrontBufferMode"    	# <i>
        #Option     "BackBufferMode"     	# <i>
        #Option     "DepthBufferMode"    	# <i>
        #Option     "OverlayBufferMode"  	# <i>
        #Option     "VideoOverlayBufferMode" 	# <i>
        #Option     "EnableIrqMgr"       	# [<bool>]
        #Option     "EnableMulticard"    	# [<bool>]
        #Option     "EnablePPLIB"        	# [<bool>]
        #Option     "DefaultOnDC"        	# [<bool>]
	Option	"DRI"	"true"
	Option	"XAANoOffscreenPixmaps"	"true"
	Identifier  "Card0"
	Driver      "fglrx"
	VendorName  "ATI Technologies Inc"
	BoardName   "Unknown Board"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24
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

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

Any ideas how to fix this? I guess the card is able to display slick fullscreen video. I know my old nvidia 6800 was...

---

### Post by HydroDiOxide on 2008-05-31
Anyone?

---

### Post by Trollslayer on 2008-05-31
> **HydroDiOxide said:**
> Anyone?

Are you using the restricted driver? The generic driver doesn't use acceleration which would explain this.

---

### Post by zeny on 2008-05-31
Hey man!

Can you give some details? Like what your testing with? 

I've got some HD movies that play like this when using VLC, but not Mplayer. So give some more details and we might be able to help further!

---

### Post by HydroDiOxide on 2008-06-04
Both HD content (mkv) and xvid are pixelated and choppy in fullscreen. I'm using the prop. ati driver (in Archlinux, by the way). I tried mplayer, but with no success.

---

