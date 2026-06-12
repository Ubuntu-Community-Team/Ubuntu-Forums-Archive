---
title: "I killed my X server ! (NVIDIA 8800 GTS)"
date: 2008-08-03
forum: Multimedia Software
---

### Post by bholliday72 on 2008-08-03
Hi,

I keep getting booted into low graphics mode with the VESA driver because i screwed up trying to install the latest NVIDIA drivers (17x) over the (169.x) drivers using envy and now everything is broken!

I have tried to uninstall the drivers through envy, uninstall the hardware drivers system GUIand  (169.x) drivers through Applications>Add/Remove, and reboot.  No such luck.  Here is my xorg.conf file.

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nv"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
EndSection

```

Here is the xorg file I had before, when I try to load it and restart x, it doesn't work, gives me an error such as "Using 173.x kernel with 169.x components".
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC FP2141SB"
    HorizSync       30.0 - 140.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS 512"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"

	# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +0+0"
	# Removed Option "metamodes" "CRT: 1280x960 +640+0, TV: 640x480 +0+0"
	# Removed Option "metamodes" "CRT: 1280x960 +0+0, TV: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1152x864 +0+0, TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by bholliday72 on 2008-08-04
I decided to reinstall Ubuntu from scratch maybe 6 months from now, hopefully no [RANDOM LOCKUPS]("http://ubuntuforums.org/showthread.php?t=877279")for me by that time.

I can't deleted / close this thread because of noob status I'm guessing.

---

### Post by KatBuntu on 2008-08-04
You would search in google: something like "reconfigure X ubuntu" instead of reinstalling.
The command for reconfiguring the X in ubuntu linux is:
```
#dpkg-reconfigure xserver-xorg
```

---

