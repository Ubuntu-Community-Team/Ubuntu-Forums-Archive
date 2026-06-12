---
title: "Problems with fglrx and video apps"
date: 2008-05-05
forum: Multimedia Software
---

### Post by Der Pate on 2008-05-05
Hi together,

I've recently upgraded to hardy, with feisty and rusty, respectivly, everything worked fine. But now I can't seem to get video apps working.

fglrx is running, also opengl ( e.g. within cedega, or simply glxgears ).

mplayer won't play videos in window mode and sometime with flickering in Fullscreen. Xine doesn't play anything at all. I've tride all the other plugins besides xv. gl and gl2 flicker all the time constantly.

Oh, my card is a Radeon 9500 and my xorg.conf is this:

```

Section "Module"
	# These modules are required for 3D acceleration
	Load "GLcore"
	Load "glx"
	Load "dri"
	# Load "extmod" but omit DGA extension
	# (the DGA extension is broken in the fglrx driver)
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
EndSection

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"logicordless"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"7"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"

# ### generic DRI settings ###
# # === disable PnP Monitor  ===
	Option                              "NoDDC"
# === disable/enable XAA/DRI ===
 	Option "no_accel"                   "no"
	Option "no_dri"                     "no"
# === misc DRI settings ===
        Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr

###//// eingeschoben von Michel
        Option "AIGLX"  "false"

### FireGL DDX driver module specific settings ###
# === Screen Management ===
	Option "DesktopSetup"               "0x00000000" 
	Option "MonitorLayout"              "AUTO, AUTO"
	Option "IgnoreEDID"                 "off"
	Option "HSync2"                     "unspecified" 
	Option "VRefresh2"                  "unspecified" 
	Option "ScreenOverlap"              "0" 

# === OpenGL specific profiles/settings ===
	Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
	Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
	Option "OpenGLOverlay"              "off"
# === Pseudo Color Visuals (8-bit visuals) ===
	Option "PseudoColorVisuals"         "off"
# === QBS Management ===
	Option "Stereo"                     "off"
	Option "StereoSyncEnable"           "1"
# === FSAA Management ===
	Option "FSAAEnable"                 "no"
	Option "FSAAScale"                  "1"
	Option "FSAADisableGamma"           "no"
	Option "FSAACustomizeMSPos"         "no"
	Option "FSAAMSPosX0"                "0.000000"
	Option "FSAAMSPosY0"                "0.000000"
	Option "FSAAMSPosX1"                "0.000000"
	Option "FSAAMSPosY1"                "0.000000"
	Option "FSAAMSPosX2"                "0.000000"
	Option "FSAAMSPosY2"                "0.000000"
	Option "FSAAMSPosX3"                "0.000000"
	Option "FSAAMSPosY3"                "0.000000"
	Option "FSAAMSPosX4"                "0.000000"
	Option "FSAAMSPosY4"                "0.000000"
	Option "FSAAMSPosX5"                "0.000000"
	Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
	Option "UseFastTLS"                 "0"
	Option "BlockSignalsOnLock"         "on"
	Option "UseInternalAGPGART"         "yes"
	Option "ForceGenericCPU"            "no"
	Option "KernelModulParm"            "agplock=0"

EndSection

Section "Extensions"
	Option		"Composite"	"1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30.0-110.0
	Vertrefresh	50.0-150.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		Viewport 0 0
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


```

The whole part about fglrx I copied from an old config. Most of it I don't even understand.

Has anyone any ideas or a reasonable howto or something?

---

### Post by Der Pate on 2008-05-07
Okay, so I'm a noob; t tokk me a while to figure out what compiz is and that it is installed, hence the issues.

Anyway, this is my xorg.conf now:

```

Section "Module"
	Load "glx"
EndSection

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"logicordless"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Buttons"		"7"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"

	Option "DRI"				"true"
	Option "ColorTiling"		"on"
	Option "EnablePageFlip"	"true"
	Option "AccelMethod" 		"EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel"		"true"
	Option "AGPMode" 		"4"
	Option "AGPFastWrite"		"on"
        Option "AIGLX"  "true"

# === Video Overlay for the Xv extension ===
	Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
	Option "OpenGLOverlay"              "off"

# === Misc Options ===
	Option "UseFastTLS"                 "2"
	Option "UseInternalAGPGART"         "yes"


EndSection

Section "Extensions"
	Option		"Composite"	"1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30.0-110.0
	Vertrefresh	50.0-150.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
#	Option "XaaNoOffscreenPixmaps" "true"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		Viewport 0 0
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


```

Also, I use fusion-icon to switch between compiz and metacity, which enables me to watch videos without problems in any application.

For further information here's a linkt to another thread concerning compiz, xv and the impending dri2 implementation

[http://ubuntuforums.org/showthread.php?t=769020]("http://ubuntuforums.org/showthread.php?t=769020")

---

### Post by ralphwiggum on 2008-05-15
Do you have any artifacts when you use opengl?  I have a radeon 9500 and am using the fglrx drivers.  Whenever an app uses opengl I get artifacts on my screen, even running glxgears they show up.

I used the fglrx driver in 7.10 and had no problems.

---

### Post by markbuntu on 2008-05-15
most likely it is compiz causing the problems but, if you are using the restricted ati drivers you can use amdcccle, the AMD Catalyst Control Center and set it to wait for vertical refresh to eliminate the tearing and flashing and other artifacts for a lot of stuff but your best bet is to get out of compiz before running these apps. 

Google Earth is especially bad at playing with compiz in fglrx. I hope they fix it soon.

---

### Post by ralphwiggum on 2008-05-16
I don't have compiz running or even installed and I still get the problems.  Maybe a driver other than the restricted one will work better.

---

