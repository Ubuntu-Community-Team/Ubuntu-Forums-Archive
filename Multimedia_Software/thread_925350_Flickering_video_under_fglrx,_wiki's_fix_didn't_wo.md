---
title: "Flickering video under fglrx, wiki's fix didn't work"
date: 2008-09-20
forum: Multimedia Software
---

### Post by missingno on 2008-09-20
I finally got fglrx to work under Hardy, which fixed the way that viewing any video would make my entire display go screwy, but now I have plenty of flickering. I tried the fix in the troubleshooting section of [this guide](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), and went to try a few games and xine, only to find that there was still flickering. [size=0]It does appear to be a tad less seizure-ish compared to before, but that might be my imagination.[/size]


My xorg.conf currently looks like this:
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Synaptics Touchpad"
	Option	    "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
	Option	    "SHMConfig" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "Centermode" "off"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "off"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option	    "TexturedXrender" "off"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
	Option       "no_accel" "no"
	Option       "no_dri" "no"
	Option       "DynamicClocks" "on"
	Option       "mtrr" "on"
	Option       "DesktopSetup" "Single"
	Option       "ScreenOverlap" "0"
	Option       "Capabilities" "0x00000000"
	Option       "CapabilitiesEx" "0x00000000"
   	Option       "PseudoColorVisuals" "off"
   	Option       "Stereo" "off"
   	Option       "StereoSyncEnable" "1"
   	Option       "FSAAEnable" "no"
   	Option       "FSAAScale" "1"
   	Option       "FSAADisableGamma" "no"
   	Option       "FSAACustomizeMSPos" "no"
   	Option       "FSAAMSPosX0" "0.000000"
   	Option       "FSAAMSPosY0" "0.000000"
   	Option       "FSAAMSPosX1" "0.000000"
   	Option       "FSAAMSPosY1" "0.000000"
   	Option       "FSAAMSPosX2" "0.000000"
   	Option       "FSAAMSPosY2" "0.000000"
   	Option       "FSAAMSPosX3" "0.000000"
   	Option       "FSAAMSPosY3" "0.000000"
   	Option       "FSAAMSPosX4" "0.000000"
   	Option       "FSAAMSPosY4" "0.000000"
   	Option       "FSAAMSPosX5" "0.000000"
   	Option       "FSAAMSPosY5" "0.000000"
   	Option       "UseFastTLS" "0"
   	Option       "BlockSignalsOnLock" "on"
   	Option       "UseInternalAGPGART" "no"
   	Option       "ForceGenericCPU" "no"
   	Option       "KernelModuleParm" "agplock=0"
   	Option       "PowerState" "1"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

```

Anyone know what I'm doing wrong here?

I know that disabling the composite extension/Compiz-fusion fixes video, but there's gotta be a way to have my cake and eat it too. I had working video and Compiz back in the days of Gutsy.

---

### Post by Brain-free on 2008-09-20
I have ATI too and have the exact same problem. I've found workarounds for it such as smplayer with X11 video output for movies or compiz-switch for games but the problem is there.

The only thing I can tell you is that usually TexturedVideo is prefered over VideoOverlay and that TexturedXrender is on. That's my two cents but I don't really thing they 'll help you much (long shot). After all, it's just two cents... ;)

---

