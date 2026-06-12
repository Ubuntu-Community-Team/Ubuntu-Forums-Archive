---
title: "Sometimes can't change screen resolution"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by jazzgossen on 2006-08-08
I have a strange screen resolution problem. Sometimes I can't change the resolution at all. 

I use the resolution dialog under System/Preferences. When it fails, the "Keep this resolution?" dialog pops up, but nothing else happens. Whether I choose to keep the new or use the old, the resolution doesn't change. Also, /var/log/Xorg.0.log doesn't show any new event. However, if I choose to change the resolution and restart X, the next time I login, the new resolution is used. I still haven't been able to find any logic as to when it works and when it doesn't. Sometimes it works, sometimes it don't. 

Another strange thing about the screen resolution dialog is that the only refresh rate that is available is 53 Hz, although my monitor is in fact using 85 Hz.

Any suggestions?

My xorg.conf follows:

```

##################################################################
#                      X Configuration File                      #
#         Created by YanC42 0.0.9 (06-08-2006 17:47:40)          #
#               (c) 2002-2005 by Sebastian J. Wolf               #
#        Licensed under GNU General Public License (GPL)         #
#     http://yanc.ygriega.de/ - http://yanc.sourceforge.net/     #
##################################################################

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
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
    Load           "type1"
    Load           "vbe"
EndSection


Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection


Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection


Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection


Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection


Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection


Section "Monitor"
    Identifier     "GDM-F520"
    Option         "DPMS"
EndSection


Section "Device"

	# Hibernate fix:
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
Option "NvAGP" "1"
Option "TwinView" "1"
Option "MetaModes" "1600x1200,1024x768@1600x1200;1280x1024,1024x768@1280x1024;1280x960,1024x768@1280x960;1152x864,1024x768@1152x864;1024x768,1024x768;800x600,800x600;640x480,640x480"
Option "TwinViewOrientation" "Clone"
Option "SecondMonitorHorizSync" "30 - 50"
Option "SecondMonitorVertRefresh" "60"
Option "TVStandard" "PAL-B"
Option "TVOutFormat" "SVIDEO"
EndSection


Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "GDM-F520"
    DefaultDepth    24
    Option         "NvAGP" "1"
	# GL performance:
    Option         "RenderAccel" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by tseliot on 2006-08-08
That might depend on Twinview.

What happens if you disable Twinview and restart the Xserver?

---

