---
title: "Dual-head problem with ATI on Edgy"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by CrowBoy1960 on 2006-11-03
Update, I've got fglrx working (thanks to post on forum re disabling Composite in xorg.conf which did the trick).

Now the remaining issue with it only detecting one screen, I get the following error in the Xorg log:

```
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Big Screen" (0)
(**) |   |-->Monitor "CMV938D"
(**) |   |-->Device "ATI Radeon, Inc. RV280 [Radeon 9200 PRO]"
(**) |-->Screen "Small Screen" (1)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "ATI Technologies, Inc. RV280 [Radeon 9200 PRO] (Secondary)"
(EE) Screen Big screen doesn't exist: deleting placement
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
```

And here is my xorg.conf:

```
Section "Files"

# path to defoma fonts
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

#Section "Monitor"
#Identifier "Laptop LCD"
#HorizSync 28.0 - 50.0
#VertRefresh 43.0 - 75.0
#Option "DPMS"
#EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	Option	    "DPMS" "true"
EndSection

#Section "Monitor"
#Identifier "aticonfig-Monitor1"
#Option "VendorName" "ATI Proprietary Driver"
#Option "ModelName" "Generic Autodetecting Monitor"
#Option "DPMS" "true"
#EndSection

Section "Monitor"
	Identifier   "CMV938D"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
Identifier "ATI Radeon, Inc. RV280 [Radeon 9200 PRO]"
Driver "fglrx"
Option "UseFBDev" "true"
Option "KernelModuleParm" "agplock=0"
Option "DesktopSetup"               "0x00000000" #dual
BusID "PCI:1:0:0"
Screen 0
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. RV280 [Radeon 9200 PRO] (Secondary)"
Driver "fglrx"
BusID "PCI:1:0:0"
Option "KernelModuleParm" "agplock=0"
Option "UseFBDev" "true"
Screen 1
EndSection



Section "Screen"
Identifier "Big Screen"
Device "ATI Radeon, Inc. RV280 [Radeon 9200 PRO]"
Monitor "CMV938D"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Section "Screen"
Identifier "Small Screen"
Device "ATI Technologies, Inc. RV280 [Radeon 9200 PRO] (Secondary)"
Monitor "SyncMaster"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Section "ServerLayout"
  
  #	InputDevice    "cursor" "SendCoreEvents"
  Identifier "Default Layout"
  screen 0 "Big Screen" 0 0
  screen 1 "Small Screen" rightof "Big screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  option "Xinerama" "on"
  option "Clone" "off"
EndSection

Section "DRI"
Mode 0666
EndSection




```

Hi all, I've upgraded (mmm, well OK, re-installed :( ) Ubuntu from 6.06 to 6.10. In 6.06 I had dual head mode kinda working, I had use of both screens but never got fglrx working properly. Since I've gone to 6.10 I can't get the dual-head working at all, even though I backed up my xorg.conf from 6.06. When I try and use the working xorg.com from 5.06 all I get is the display on the secondary (15") monitor. No matter what I do to the xorg.conf it insists on only using the 15" leaving a blank 17" screen :(. I just wondered if any one else had similar issues and even better if anyone has a solution.

Thanks,
Martin

---

### Post by danieldobs on 2006-11-08
Hi, I have a similar problem ..

I would like my laptop to run it's native resolution while my TV runs 800x600 .. so that i can watch DIVX on TV 

I got dual heads working, but when i drag the VIDEO from my lappie to my tv i lose picture (screen is black) i tried overlay = 1 from aticonfig .. i don't know what to do? please help!?

---

