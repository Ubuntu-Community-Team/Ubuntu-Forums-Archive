---
title: "Upgraded Edgy to Feisty Dual Monitors Do not Work"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by gbaker386 on 2007-04-26
I upgraded from Edgy to Feisty and after rebooting I noted that my dual monitors were not displaying one merged frame buffer.  This is a feature of the open source ATI driver that I have configured in my xorg.conf file.

I have modified my file many different ways but it seems like Xorg is ignoring the changes.  I know the file worked prior to the upgrade so is there something different required when running feisty?

Here is my xorg.conf file (/etc/X11/xorg.conf) does anyone have any advice?  (note I added some of the options under the ATI device block after rebooting into feisty and seeing that the dual monitors were not merged)

> Section "ServerLayout"
    Option         "AIGLX"  "true"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
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
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "drm"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
    Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
    Option      "Resolution" "1600"
EndSection

Section "Monitor"
	Identifier   "BenQ T701"
	HorizSync    31.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
    Identifier  "ATI 9250"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
    Option      "XaaNoOffscreenPixmaps"
    Option      "AGPMode"           "8"
    Option      "AGRFastWrite"      "true"
    Option "DisableGLXRootClipping" "true"
    Option "AddARGBGLXVisuals" "true"
    Option "AllowGLXWithComposite" "true"
    Option      "EnablePageFlip"    "on"
    Option      "RenderAccel"       "on"
    Option      "AccelMethod"       "EXA" # or XXA
#   Option      "BackingStore"      "true"
#   Option      "ExaNoOffscreenPixmaps"
    # enable (partial) PowerPlay features
#    Option      "DynamicClocks"     "on"
    # enable radeon specific xinerama
    Option  "MergedFB"              "true"
    Option  "CRT2Position"          "LeftOf"
    Option  "CRT2Hsync"             "31-81"
    Option  "CRT2VRefresh"          "56-75"
    Option  "MonitorLayout"         "LCD, CRT"
    Option  "MetaModes"             "1280x1024-1280x1024"
# used when I want to use beryl
#    Option  "MetaModes"            "1024x768-1024x768"
#    does nothing??
#    Option  "MergedXinerama"       "on"
    Option  "MergedNonRectangular"  "false"
    # Color Tiling
    Option      "ColorTiling"       "on"
    # Video overlay
    Option      "OverlayOnCRTC2"    "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI 9250"
	Monitor    "BenQ T701"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "dri"
	Mode         0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

---

