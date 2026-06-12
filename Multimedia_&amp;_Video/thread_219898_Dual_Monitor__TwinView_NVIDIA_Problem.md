---
title: "Dual Monitor / TwinView NVIDIA Problem"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by s_d on 2006-07-20
Hi

I have a GeForce 7800 GT card with two monitors connected to it, one 24" and one 20". I would like the 24" to be the primary, and then extend the desktop to the 20". I think I've managed to do everything _but_ that. At present the 20" is primary and the desktop extends to the 24". The total resolution is 3520x1200, but I think the resolutions are reversed so that the 20" is 1920x1200 and the 24" is 1600x1200. But I might be wrong.

With my very limited knowledge, just about everything I try, including "UseDisplayDevice" and "ConnectedMonitor", ends up with just the 24" working at 1600x1200.

Does anyone have any ideas on changing the displays, or correcting what ever is wrong? 

Here is my xorg.conf file:

---------------------

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
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
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
    Identifier     "DELL 2405FPW"
    Option         "DPMS"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option	   "ConnectedMonitor" "DFP,LCD"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DELL 2405FPW"
    DefaultDepth    24
    Option         "TwinView"
    Option         "MetaModes" "1600x1200, 1920x1200; 1280x1024, 1280x1024; 1280x1024, 1152x864; 1024x768, 1024x768; NULL,1680x1050; NULL,1280x1024; NULL,1152x864; NULL,1024x768"
    Option         "SecondMonitorHorizSync" "31-85"
    Option         "SecondMonitorVertRefresh" "55-85"
    Option         "TwinViewOrientation" "RightOf"
    Option         "RenderAccel" "true"
    Option         "AGPFastWrite" "true"
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by caravela on 2006-07-20
does that Config even works ?? 
all of twinview should be allong with the device (the grafic card) 
as for the problem i have the same one. Reading the readme that comes with the drivers there is one possible solution, it is to tell the driver exactly wich one is first and wich one is second.
[Readme]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-g.html")

see this options 
  Option "TwinViewOrientation"      "CRT-0 LeftOf DFP-0"
 Option "ConnectedMonitor" "CRT, CRT"
in my case i had to put
Option "TwinViewOrientation"      "CRT-1 LeftOf DFP"
Option "ConnectedMonitor" "DFP, CRT-1"
check the readme :)

Edit:
on the [http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-d.html"] readme]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-d.html") it says 
"Option "UseDisplayDevice" "string"

    When assigning display devices to X screens, the NVIDIA X driver by default assigns display devices in the order they are found (looking first at CRTs, then at DFPs, and finally at TVs). This option can be used to override this assignment. For example, if both a CRT and a DFP are connected, you could specify:

        Option "UseDisplayDevice" "DFP"

    to make the X screen use the DFP, even though it would have used a CRT by default.

    Note the subtle difference between this option and the "ConnectedMonitor" option: the "ConnectedMonitor" option overrides what display devices are actually detected, while the "UseDisplayDevice" option controls which of the detected display devices will be used on this X screen.
"

tried it, it does set the primary display but in my case the other monitor goes blank.

---

### Post by s_d on 2006-07-21
Yes, it does. So I guess it's not that important where you put stuff..

I've tried both "ConnectedMonitor" and "UseDisplayDevice", and they end up with the same result you got. One blank screen. In my case the 20". I've even tried specifying "MetaModes" to "DFP-0: 1920x1200, DFP-1: 1600x1200;". But still I end up with just the 24" working. 

It would seem the 20" is set as primary by default. But when I specify the 24" as primary, the 20" can't handle being secondary.

---

