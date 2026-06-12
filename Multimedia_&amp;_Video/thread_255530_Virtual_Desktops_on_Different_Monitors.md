---
title: "Virtual Desktops on Different Monitors?"
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by jmorgan on 2006-09-11
I was wondering if anyone had any advice on setting up a multi-monitor display to show different desktops on each monitor with Kubuntu.

All the howto's I've seen only address showing one large desktop spanned across multiple monitors.  I don't find any utility to having a window span multiple monitors.  I have a 19" flatscreen and two 17" crts.  They can all display at 1280x1024 but I don't want the sudden shift that occurs when jumping between displays or the jump between screens when I try to 

What I would like to have set up is similar to the virtual desktop functionality of KDE except each monitor is a "real" desktop all within the same system (one mouse, one keyboard) that I can switch between with a hotkey (ctrl-F1, ctrl-F2...) etc.  

I was wondering if this was at all possible and if so what should I use?  I know this isn't the default behavior of xinerama since I've tried it, unless there are some settings I don't know about.  I haven't tried Twinview (I do have all nvidia cards).  What is this the default behavior of kde without using xinerama?  I was under the impression that it simply cloned the same thing across multiple screens.

Does anyone have any advice?

---

### Post by Ziox on 2006-09-11
> **jmorgan said:**
> I was wondering if anyone had any advice on setting up a multi-monitor display to show different desktops on each monitor with Kubuntu.

All the howto's I've seen only address showing one large desktop spanned across multiple monitors.  I don't find any utility to having a window span multiple monitors.  I have a 19" flatscreen and two 17" crts.  They can all display at 1280x1024 but I don't want the sudden shift that occurs when jumping between displays or the jump between screens when I try to 

What I would like to have set up is similar to the virtual desktop functionality of KDE except each monitor is a "real" desktop all within the same system (one mouse, one keyboard) that I can switch between with a hotkey (ctrl-F1, ctrl-F2...) etc.  

I was wondering if this was at all possible and if so what should I use?  I know this isn't the default behavior of xinerama since I've tried it, unless there are some settings I don't know about.  I haven't tried Twinview (I do have all nvidia cards).  What is this the default behavior of kde without using xinerama?  I was under the impression that it simply cloned the same thing across multiple screens.

Does anyone have any advice?

I know there is a way to setup two different sessions, where you can move cursor b/t the monitors, but not drag windows between them....basically to enable it....just setup Xinerama correctly, but without enabling Xinerama...

---

### Post by jmorgan on 2006-09-11
Thank you this is close to what I want.  It does show two desktops like I want instead of 1 large virtual desktop, however, the mouse travels too freely between them.  Do you know of any way to limit the mouse jumping between screens so freely.  Maybe a delay to switch screens or a hotkey.  I could live without it though, but it has been bugging me.

I do have a more serious problem though.  The resolution on the second screen is significantly less than the resolution on the first.  I have it working through modifying the xorg.conf as displayed below 

```

Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
  identifier "Right NVIDIA Corporation GeForce 6200"
  boardname "nv"
  busid "PCI:0:10:0"
  driver "nv"
  screen 0
EndSection

Section "Monitor"
  identifier "Right Monitor"
  modelname "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Right Screen"
  Device "Right NVIDIA Corporation GeForce 6200"
  Monitor "Right Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1280x960@60" "1280x854" "1152x768@54" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Right Screen" 0 0
  screen 1 "Left Screen" leftof "Right Screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" # 
  identifier "device1"
  boardname "nv"
  busid "PCI:0:10:0"
  driver "nv"
  screen 1
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "device" # 
  identifier "device2"
  boardname "NVIDIA GeForce 6800 (generic)"
  busid "PCI:0:11:0"
  driver "nv"
  screen 0
  vendorname "NVIDIA"
EndSection
Section "screen" # 
  identifier "Left Screen"
  device "device2"
  defaultdepth 24
  monitor "monitor2"
EndSection
Section "monitor" # 
  identifier "monitor2"
  gamma 1.0
EndSection
Section "device" # 
  identifier "device3"
  boardname "NVIDIA GeForce FX (generic)"
  busid "PCI:1:0:0"
  driver "nv"
  screen 0
  vendorname "NVIDIA"
EndSection
Section "screen" # 
  identifier "screen3"
  device "device3"
  defaultdepth 24
  monitor "monitor3"
EndSection
Section "monitor" # 
  identifier "monitor3"
  gamma 1.0
EndSection
Section "ServerFlags"
  option "Xinerama" "false"
EndSection

``` 

I used your howto for xinerama and modified my xorg.conf but the second monitor (the left doesn't show up at all)  Both monitors and pci video cards are the same model.   It looks like the following.
```


Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
  identifier "Right NVIDIA Corporation GeForce 6200"
  boardname "nv"
  busid "PCI:0:10:0"
  driver "nv"
  screen 0
  Option "MonitorLayout" "CRT, CRT"
EndSection

Section "Device"
  identifier "Left NVIDIA Corporation GeForce 6200"
  boardname "nv"
  busid "PCI:0:11:0"
  driver "nv"
  screen 1
  Option "MonitorLayout" "CRT, CRT"
EndSection

Section "Monitor"
  identifier "Right Monitor"
  modelname "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Monitor"
  identifier "Left Monitor"
  modelname "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Right Screen"
  Device "Right NVIDIA Corporation GeForce 6200"
  Monitor "Right Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1280x960@60" "1280x854" "1152x768@54" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection

Section "Screen"
  Identifier "Left Screen"
  Device "Left NVIDIA Corporation GeForce 6200"
  Monitor "Left Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1280x960@60" "1280x854" "1152x768@54" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection

#Section "ServerFlags"
#  option "Xinerama" "true"
#EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Right Screen" 0 0
  screen 1 "Left Screen" leftof "Right Screen"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

#Section "DRI"
#  Mode 0666
#EndSection

```

I also checked the /var/log/Xorg.log file and get no error messags.  Any ideas?

---

### Post by Ziox on 2006-09-11
I think that "Option MonitorLayout" is specific to the radeon driver...try "man nv"...

no errors from xorg log?

cat /var/log/Xorg.0.log | grep EE

cat /var/log/Xorg.0.log | grep WW

---

### Post by jmorgan on 2006-09-11
You are correct there is no options for MonitorLayout so I removed the option and restarted X then checked your commands

```

Current Operating System: Linux jmorgan-desktop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
(EE) Screen 1 deleted because of no matching config section.
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

and 

```


        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) NV: No matching Device section for instance (BusID PCI:0:11:0) found
(WW) NV: No matching Device section for instance (BusID PCI:1:0:0) found
(WW) (640x480@60,Right Monitor) mode clock 25.2MHz exceeds DDC maximum 0MHz
(WW) (800x600@56,Right Monitor) mode clock 36MHz exceeds DDC maximum 0MHz
(WW) (800x600@60,Right Monitor) mode clock 40MHz exceeds DDC maximum 0MHz
(WW) (1024x768@60,Right Monitor) mode clock 65MHz exceeds DDC maximum 0MHz
(WW) (1152x768@54,Right Monitor) mode clock 64.995MHz exceeds DDC maximum 0MHz
(WW) (1280x854,Right Monitor) mode clock 80MHz exceeds DDC maximum 0MHz
(WW) (1280x960@60,Right Monitor) mode clock 102.1MHz exceeds DDC maximum 0MHz
(WW) (1280x1024@60,Right Monitor) mode clock 108MHz exceeds DDC maximum 0MHz
(WW) (640x350,Right Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x175,Right Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (640x400,Right Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x200,Right Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (720x400,Right Monitor) mode clock 35.5MHz exceeds DDC maximum 0MHz
(WW) (360x200,Right Monitor) mode clock 17.75MHz exceeds DDC maximum 0MHz
(WW) (640x480,Right Monitor) mode clock 25.2MHz exceeds DDC maximum 0MHz
(WW) (320x240,Right Monitor) mode clock 12.6MHz exceeds DDC maximum 0MHz
(WW) (640x480,Right Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x240,Right Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (640x480,Right Monitor) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x240,Right Monitor) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (640x480,Right Monitor) mode clock 36MHz exceeds DDC maximum 0MHz
(WW) (320x240,Right Monitor) mode clock 18MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 36MHz exceeds DDC maximum 0MHz
(WW) (400x300,Right Monitor) mode clock 18MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 40MHz exceeds DDC maximum 0MHz
(WW) (400x300,Right Monitor) mode clock 20MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 50MHz exceeds DDC maximum 0MHz
(WW) (400x300,Right Monitor) mode clock 25MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 49.5MHz exceeds DDC maximum 0MHz
(WW) (400x300,Right Monitor) mode clock 24.75MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 56.3MHz exceeds DDC maximum 0MHz
(WW) (400x300,Right Monitor) mode clock 28.15MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Right Monitor) mode clock 44.9MHz exceeds DDC maximum 0MHz
(WW) (512x384,Right Monitor) mode clock 22.45MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Right Monitor) mode clock 65MHz exceeds DDC maximum 0MHz
(WW) (512x384,Right Monitor) mode clock 32.5MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Right Monitor) mode clock 75MHz exceeds DDC maximum 0MHz
(WW) (512x384,Right Monitor) mode clock 37.5MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Right Monitor) mode clock 78.8MHz exceeds DDC maximum 0MHz
(WW) (512x384,Right Monitor) mode clock 39.4MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Right Monitor) mode clock 94.5MHz exceeds DDC maximum 0MHz
(WW) (512x384,Right Monitor) mode clock 47.25MHz exceeds DDC maximum 0MHz
(WW) (1152x864,Right Monitor) mode clock 108MHz exceeds DDC maximum 0MHz
(WW) (576x432,Right Monitor) mode clock 54MHz exceeds DDC maximum 0MHz
(WW) (1280x960,Right Monitor) mode clock 108MHz exceeds DDC maximum 0MHz
(WW) (640x480,Right Monitor) mode clock 54MHz exceeds DDC maximum 0MHz
(WW) (1280x960,Right Monitor) mode clock 148.5MHz exceeds DDC maximum 0MHz
(WW) (640x480,Right Monitor) mode clock 74.25MHz exceeds DDC maximum 0MHz
(WW) (1280x1024,Right Monitor) mode clock 108MHz exceeds DDC maximum 0MHz
(WW) (640x512,Right Monitor) mode clock 54MHz exceeds DDC maximum 0MHz
(WW) (1280x1024,Right Monitor) mode clock 135MHz exceeds DDC maximum 0MHz
(WW) (640x512,Right Monitor) mode clock 67.5MHz exceeds DDC maximum 0MHz
(WW) (1280x1024,Right Monitor) mode clock 157.5MHz exceeds DDC maximum 0MHz
(WW) (640x512,Right Monitor) mode clock 78.75MHz exceeds DDC maximum 0MHz
(WW) (1600x1200,Right Monitor) mode clock 162MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 81MHz exceeds DDC maximum 0MHz
(WW) (1600x1200,Right Monitor) mode clock 175.5MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 87.75MHz exceeds DDC maximum 0MHz
(WW) (1600x1200,Right Monitor) mode clock 189MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 94.5MHz exceeds DDC maximum 0MHz
(WW) (1600x1200,Right Monitor) mode clock 202.5MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 101.25MHz exceeds DDC maximum 0MHz
(WW) (1600x1200,Right Monitor) mode clock 229.5MHz exceeds DDC maximum 0MHz
(WW) (800x600,Right Monitor) mode clock 114.75MHz exceeds DDC maximum 0MHz
(WW) (1792x1344,Right Monitor) mode clock 204.8MHz exceeds DDC maximum 0MHz
(WW) (896x672,Right Monitor) mode clock 102.4MHz exceeds DDC maximum 0MHz
(WW) (1792x1344,Right Monitor) mode clock 261MHz exceeds DDC maximum 0MHz
(WW) (896x672,Right Monitor) mode clock 130.5MHz exceeds DDC maximum 0MHz
(WW) (1856x1392,Right Monitor) mode clock 218.3MHz exceeds DDC maximum 0MHz
(WW) (928x696,Right Monitor) mode clock 109.15MHz exceeds DDC maximum 0MHz
(WW) (1856x1392,Right Monitor) mode clock 288MHz exceeds DDC maximum 0MHz
(WW) (928x696,Right Monitor) mode clock 144MHz exceeds DDC maximum 0MHz
(WW) (1920x1440,Right Monitor) mode clock 234MHz exceeds DDC maximum 0MHz
(WW) (960x720,Right Monitor) mode clock 117MHz exceeds DDC maximum 0MHz
(WW) (1920x1440,Right Monitor) mode clock 297MHz exceeds DDC maximum 0MHz
(WW) (960x720,Right Monitor) mode clock 148.5MHz exceeds DDC maximum 0MHz
(WW) (832x624,Right Monitor) mode clock 57.284MHz exceeds DDC maximum 0MHz
(WW) (416x312,Right Monitor) mode clock 28.642MHz exceeds DDC maximum 0MHz
(WW) (1280x768,Right Monitor) mode clock 80.14MHz exceeds DDC maximum 0MHz
(WW) (640x384,Right Monitor) mode clock 40.07MHz exceeds DDC maximum 0MHz
(WW) (1280x800,Right Monitor) mode clock 83.46MHz exceeds DDC maximum 0MHz
(WW) (640x400,Right Monitor) mode clock 41.73MHz exceeds DDC maximum 0MHz
(WW) (1152x768,Right Monitor) mode clock 64.995MHz exceeds DDC maximum 0MHz
(WW) (576x384,Right Monitor) mode clock 32.497MHz exceeds DDC maximum 0MHz
(WW) (1152x864,Right Monitor) mode clock 121.5MHz exceeds DDC maximum 0MHz
(WW) (576x432,Right Monitor) mode clock 60.75MHz exceeds DDC maximum 0MHz
(WW) (1400x1050,Right Monitor) mode clock 122MHz exceeds DDC maximum 0MHz
(WW) (700x525,Right Monitor) mode clock 61MHz exceeds DDC maximum 0MHz
(WW) (1400x1050,Right Monitor) mode clock 151MHz exceeds DDC maximum 0MHz
(WW) (700x525,Right Monitor) mode clock 75.5MHz exceeds DDC maximum 0MHz
(WW) (1400x1050,Right Monitor) mode clock 155.8MHz exceeds DDC maximum 0MHz
(WW) (700x525,Right Monitor) mode clock 77.9MHz exceeds DDC maximum 0MHz
(WW) (1400x1050,Right Monitor) mode clock 184MHz exceeds DDC maximum 0MHz
(WW) (700x525,Right Monitor) mode clock 92MHz exceeds DDC maximum 0MHz
(WW) (1440x900,Right Monitor) mode clock 108.84MHz exceeds DDC maximum 0MHz
(WW) (720x450,Right Monitor) mode clock 54.42MHz exceeds DDC maximum 0MHz
(WW) (1600x1024,Right Monitor) mode clock 106.91MHz exceeds DDC maximum 0MHz
(WW) (800x512,Right Monitor) mode clock 53.455MHz exceeds DDC maximum 0MHz
(WW) (1680x1050,Right Monitor) mode clock 147.14MHz exceeds DDC maximum 0MHz
(WW) (840x525,Right Monitor) mode clock 73.57MHz exceeds DDC maximum 0MHz
(WW) (1680x1050,Right Monitor) mode clock 146.25MHz exceeds DDC maximum 0MHz
(WW) (840x525,Right Monitor) mode clock 73.125MHz exceeds DDC maximum 0MHz
(WW) (1680x1050,Right Monitor) mode clock 214.51MHz exceeds DDC maximum 0MHz
(WW) (840x525,Right Monitor) mode clock 107.255MHz exceeds DDC maximum 0MHz
(WW) (1920x1200,Right Monitor) mode clock 193.16MHz exceeds DDC maximum 0MHz
(WW) (960x600,Right Monitor) mode clock 96.58MHz exceeds DDC maximum 0MHz
(WW) (1920x1200,Right Monitor) mode clock 230MHz exceeds DDC maximum 0MHz
(WW) (960x600,Right Monitor) mode clock 115MHz exceeds DDC maximum 0MHz
(WW) (1920x1440,Right Monitor) mode clock 341.35MHz exceeds DDC maximum 0MHz
(WW) (960x720,Right Monitor) mode clock 170.675MHz exceeds DDC maximum 0MHz
(WW) (2048x1536,Right Monitor) mode clock 266.95MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Right Monitor) mode clock 133.475MHz exceeds DDC maximum 0MHz
(WW) (2048x1536,Right Monitor) mode clock 340.48MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Right Monitor) mode clock 170.24MHz exceeds DDC maximum 0MHz
(WW) (2048x1536,Right Monitor) mode clock 388.04MHz exceeds DDC maximum 0MHz
(WW) (1024x768,Right Monitor) mode clock 194.02MHz exceeds DDC maximum 0MHz


```

PCI:0:11:0 is the Left monitor, screen, and device.  It is defined, I'm not sure why it's not working, I've checked it over for typos several times.  

BusID PCI:1:0:0 is actually an agp video card hooked up to a flat panel that I don't have connected yet.  I want to eventually have a three monitor setup (with the flat panel in the center) but I'm trying to take it one step at a time and get the (supposedly) easier identical CRTs set up.

Any ideas about the errors?  Thank you so much for your help so far.

---

### Post by jmorgan on 2006-09-12
Reading the x.org wiki FAQMiscellaneous I believe the answer lies in that I have screen 0 and screen 1 specified which would imply that they are running off a dual head card.  I, however, am running two seperate pci video cards so I think both should be 0.

---

### Post by jmorgan on 2006-09-12
Anyone have any ideas on how to set up the third monitor?

Is is as simple as copying the Device, Monitor, and Screen sections, replacing them with the correct identifiers, then adding:
```

  screen 2 "x" rightof "y"

```

I can only hope...

---

### Post by elitegoodguy on 2006-11-09
Where you able to figure this out?  I am having the exact same issue as you.  The only difference is that I am trying to run it with 2 monitors.  I'm getting the 

(EE) Screen 1 deleted because of no matching config section.

Thanks

---

