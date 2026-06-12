---
title: "60 Hz 1080p LCD question"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by xturmn8r on 2007-07-25
Hey cats, 

I've been goofing with my xorg.conf for a while, and I can't seem to get my Screen Resolution menu to display 60 Hz, but rather it says 50 or 56.  I'd like to have it at 60, so if I could get someone to look at it, I'd be very happy!

> Section "ServerLayout"
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
    Identifier     "LVM-47W1"
    HorizSync       31.5 - 90.0
    VertRefresh     60.0 - 60.0
    ModeLine "1920x1080" 148.5 1920 2024 2072 2200 1080 1084 1094 1124 -hsync -vsync
    Option "ModeValidation" "NoMaxPClkCheck, NoEdidMaxPClkCheck"
    Option "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 Series GPU]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40 [GeForce 6800 Series GPU]"
    Monitor        "LVM-47W1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


---

### Post by MrHippocampus on 2007-07-25
Try running nvidia-settings and see what that says the Hz value is.

---

### Post by xturmn8r on 2007-07-25
I was able to set the refresh rate thru that, thanks!  

:popcorn:

---

