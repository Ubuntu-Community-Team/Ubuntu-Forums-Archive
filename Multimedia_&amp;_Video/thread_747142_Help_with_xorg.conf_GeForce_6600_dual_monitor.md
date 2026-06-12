---
title: "Help with xorg.conf GeForce 6600 dual monitor"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by mtpocket2 on 2008-04-06
I have a GeForce 6600 dual head card I am trying to get to work with dual monitors.   The monitors are both SyncMaster 930b's, one analog one digital.  The analog one is the only one working.  This is a dual boot machine so I know the hardware is good as everything works in XP.  I see people posting many different configs and below is the way the nvidia software configured mine.  Can someone take a look and let me know whats missing.  Thanks for your help.


Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "TwinViewXineramaInfoOrder" "DFP-1 CRT-0"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT-0: nvidia-auto-select +0+0, DFP: 1280x1024 +1280+0"
# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0, DFP-1: 1280x1024 +1280+0"
# Removed Option "TwinView" "1"
# Removed Option "TwinViewXineramaInfoOrder" "CRT-0, DFP-1"
# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0, DFP: 1280x1024 +1280+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT-0: 1280x1024 +0+0"
# Removed Option "metamodes" "CRT-0: 1280x1024 +1280+0, DFP: 1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseDisplayDevice" "CRT-0, DFP-1"
    Option         "TwinViewOrientation" "DFP-1 RightOf CRT-0"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0, DFP-1"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, DFP: 1280x1024 +1280+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1280x1024 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

