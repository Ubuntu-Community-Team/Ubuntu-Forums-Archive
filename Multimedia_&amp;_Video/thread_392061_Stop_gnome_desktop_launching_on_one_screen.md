---
title: "Stop gnome desktop launching on one screen"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by cartel on 2007-03-24
Hello all,

My "dream" NVIDIA dualhead config is having Freevo running on my TV out (controlled via lirc) with the Ubuntu desktop on my monitor.

So far the best I can come up with is running the X server in dual screen mode (not twinview), this results in a seperate session being spawned on the TV. This session runs gnome.

Is there any way to make it not run gnome, and instead launch a script? Optimally Freevo should launch when GDM starts. Is this doable? I've been googling around and found no way to prevent GDM managing a screen, or no way to prevent Gnome launching on one screen and not the other.

For reference here is my xorg.conf

```
Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Device"
    Identifier     "VGA"
    Driver         "nvidia"
    Screen	   0
    BusID	   "PCI:1:0:0"
EndSection

Section "Device" 
 Identifier  "TVOUT"
 Driver      "nvidia"
 Option      "TVOutFormat" "COMPOSITE"  # Or "SVIDEO"
 Option      "TVStandard" "PAL-B"
 Option      "ConnectedMonitor" "TV"
 Screen	     1
 BusID       "PCI:1:0:0"
EndSection



Section "Monitor"
    Identifier     "p110"
    HorizSync       30.0 - 130.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "aquos"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0 - 60.0
EndSection


Section "Screen"
    Identifier     "monitor"
    Device         "VGA"
    Monitor        "p110"
    DefaultDepth    24
    Option         "NvAGP" "3"
    Option         "DigitalVibrance" "1"
    Option         "TransparentIndex" "0"
    Option         "CursorShadowAlpha" "64"
    Option         "CursorShadowXOffse" "4"
    Option         "CursorShadowYOffset" "2"
    Option         "NoLogo" "TRUE"
#    Option         "Twinview" "TRUE"
    #Option         "TwinViewOrientation" "Clone"
#    Option         "SecondMonitorHorizSync" "60"
#    Option         "SecondMonitorVertRefresh" "60"
#    Option         "MetaModes" "1024x768, 1024x768"
#    Option         "ConnectedMonitor" "p110, bravia"
#    Option         "TVStandard" "PAL-B"
#    Option         "TVOutFormat" "Composite"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
 Identifier "tv"
 Device     "TVOUT"
 Monitor    "aquos"
 DefaultDepth 16
 SubSection "Display"
 Depth     24
 Modes "1280x1024" "1152x864" "1024x768" "800x600"
 EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "seperate"
    Screen 0       "monitor"
    Screen 1	   "tv" LeftOf "monitor"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection
```

Dont think its Xorg's fault that gnome is launching on both screens, suspect its gdm.

Perhaps I could use a custom .xsession file and avoid gnome starting on both screens?

Will keep trying, in the mean time any help appreciated...

---

### Post by cartel on 2007-03-24
Bump: I've been playing around using the failsafe session, as soon as i start gnome-panel or gnome-session both screens are taken over regardless of --display or export DISPLAY= pleading.

A halfway passable solution seems to be to just delete the panels on the second monitor and set a black background. Unfortunately the background/panel settings for multiple screens are forgotten when I restart the session :(.

Perhaps I could switch to a more cooperative desktop/window manager (thinking of trying kde) that might support disabling management of a secondary screen...

---

