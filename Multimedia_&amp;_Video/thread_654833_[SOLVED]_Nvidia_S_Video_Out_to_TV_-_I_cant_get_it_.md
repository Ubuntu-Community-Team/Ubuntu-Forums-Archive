---
title: "[SOLVED] Nvidia S Video Out to TV - I cant get it to work!"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by thebrandon on 2007-12-31
I have an NVIDIA Geforce4 MX 4000 and I want to basically run the same thing my monitor displays on my tv at the same time.  I definitely have my card installed properly and when I try to enable the tv in the X Server Settings menu the settings wont stick when I reboot and the TV is always disabled.  Any help would be greatly appreciated!  Thanks!

---

### Post by johnsonfarms on 2007-12-31
i had similar difficulties with my nvidia card. I followed this description [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo) and had reasonable succes but i did not understand well enough to have separate resolution for my monitor and tv so my tv looked great but my comp looked out of whack. If you can figure it all out it will work fine.

---

### Post by thebrandon on 2008-01-01
Well, I am still fighting with it, I finally got it to display on my TV but the problem is that after I make the changes to my xorg.conf file and restart my x server it messes up my resolution and locks it at 800 x 600 and Ive got this wierd zoom effect on my desktop where I cant even access the taskbar at the bottom of my screen!  I dont understand why no matter what I change I cant seem to fix it properly!

Here is the xorg.conf that I made to run the TV-out :
```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CorePointer"
    InputDevice    "Configured Mouse" "CoreKeyboard"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
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
    Identifier     "Monitor[0]" #CRT
    VendorName     "Sony"
    ModelName      "Sony SDM-M51"
    HorizSync       28.0 - 61.0
    VertRefresh     48.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor[1]" #TV
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    HorizSync       30 - 50
    VertRefresh     50 - 60
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce4 (generic)"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device[1]"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce4 (generic)"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "TwinView" "true"
    Option         "TwinViewOrientation" "Clone"
    Option         "TVOutFormat" "SVIDEO" #or SVIDEO etc 
    Option         "TVStandard" "NTSC-M" #or NTSC etc 
    Option         "SecondMonitorHorizSync" "30-50"
    Option         "SecondMonitorVertRefresh" "60"
    Option         "ConnectedMonitor" "Monitor[1]" 
    Option         "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480"
    BusID          "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]" 
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1024 768 
        Depth       24
        Modes      "1024x768@60" "640x480@60" "800x600@56" "800x600@60" "1280x960@60"
    EndSubSection
EndSection

Section "Screen" 
   Identifier      "Screen[1]"
   Device          "Device[1]"  
   Monitor         "Monitor[1]" 
   DefaultDepth     24 
   SubSection      "Display" 
         Depth      24 
         Modes     "640x480@60" 
   EndSubSection    
EndSection
```

And here is my original xorg.conf with the settings correct
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
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
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SDM-M51"
    Option         "DPMS"
    HorizSync      28-61 
    VertRefresh    48-65

EndSection

Section "Device"
    Identifier     "nVidia Corporation NV18 [GeForce4 MX 4000]"
    Driver         "nvidia"
    Option "AddARGBGLXVisuals" "True"
    Option "RenderAccel" "True"
    Option "AllowGLXWithComposite" "True"
    Option "backingstore" "True"
    Option "TripleBuffer" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV18 [GeForce4 MX 4000]"
    Monitor        "SDM-M51"
    DefaultDepth    24
    Option "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "720x400" "640x480" "640x400"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```


I even tried rewriting everything a different way with the same results :
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0  
    Screen         "TV Screen" 
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
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
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SDM-M51"
    Option         "DPMS"
    HorizSync      28-61 
    VertRefresh    48-65

EndSection

Section "Monitor"
    Identifier	   "SonyTV"
    HorizSync       30 - 50
    VertRefresh     50 - 60
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV18 [GeForce4 MX 4000]"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
EndSection

Section "Device"
    Identifier      "DeviceTV"
    Driver          "nvidia"
    Option          "TVOutFormat" "SVIDEO"
    Option          "TVStandard" "NTSC-M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV18 [GeForce4 MX 4000]"
    Monitor        "SDM-M51"
    DefaultDepth    24
    Option "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "720x400" "640x480" "640x400"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "TV Screen"
    Device         "SonyTV"
    Monitor        "DeviceTV"
    DefaultDepth    24
    Option "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "720x400" "640x480" "640x400"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "720x400" "640x480" "640x400"
    EndSubSection
EndSection


Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by johnsonfarms on 2008-01-01
That is the exact problem I had, not sure how to fix it. Hopefully someone else will have an idea for you (and me).

---

### Post by thebrandon on 2008-01-01
Yeah, I hope so too, I am digging all over the place trying to find a solution but thus far you are the only other person I have come upon with this problem.  If I figure anything out I will let you know!

---

### Post by thebrandon on 2008-01-01
Well, I finally figured it out and it was so simple it is embarrasing!  All you have to do is add the following lines into your Section "Device" below whatever entries you already have : 

   Option "TwinView" "true"
   Option "TwinViewOrientation" "Clone"
   Option "TVOutFormat" "S-VIDEO"
   Option "TVStandard" "NTSC-M"
   Option "SecondMonitorHorizSync" "30-50"
   Option "SecondMonitorVertRefresh" "60"
   Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384" 

And its as simple as that!

---

### Post by johnsonfarms on 2008-01-01
glad you got it working, i'll have to give that a try. thanks.

---

