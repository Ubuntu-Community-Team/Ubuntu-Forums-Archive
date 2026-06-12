---
title: "ViewSonic VG2021m - Vertical fuzzy lines"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by acl123 on 2007-09-12
Hi,
I am getting vertical 3-4cm wide fuzzy lines on my monitor and I'm having trouble getting rid of them.

I have a ViewSonic vg2021m and GEForce 7300 GS. I installed the latter with Envy.
My screen resolution is set at 1400/1050/60 which is the recommended resolution.

I have played with my xorg.conf a bit but the problem won't go away.

I added the line "Option "ModeValidation" "NoEdidDFPMaxSizeCheck"" in the device section. I'm not really sure what this does, but I got the advice from this post: [http://www.linuxquestions.org/questions/showthread.php?t=579933](http://www.linuxquestions.org/questions/showthread.php?t=579933)

I also setup the Monitor section using advice from a couple of different web pages.

This is my xorg.conf:

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
    Identifier     "Monitor0"
    VendorName     "Viewsonic"
    ModelName      "VG2021m"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Modeline       "1400x1050_60.00"  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -HSync +Vsync
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7300 GS]"
    Driver         "nvidia"
    Option "ModeValidation" "NoEdidDFPMaxSizeCheck"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7300 GS]"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Any insight would be appreciated. Thanks

---

