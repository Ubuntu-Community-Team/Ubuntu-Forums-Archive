---
title: "Dual Monitor, AGP and PCI, almost there, one final step!"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by jazzman14 on 2007-12-24
Okay, I have it all set up, however, there is a problem. My cursor starts on my left monitor, and once it moves to the right monitor, you can't get it to go back to the left monitor. Also the task bars on top and bottom are on both monitors. Finally, when you open System|Administration|Screens And Graphics, it restarts x.

Here is my xorg.conf:

```
Section "ServerLayout"
       Identifier     "X.org Configured"
       Screen      0  "Screen0" 0 0
       Screen      1  "Screen1" RightOf "Screen0"
       Screen      0  "Screen0" LeftOf "Screen1"
       InputDevice    "Generic Keyboard"
       InputDevice    "Configured Mouse"
EndSection

Section "Files"
       RgbPath      "/etc/X11/rgb"
       ModulePath   "/usr/lib/xorg/modules"
       FontPath     "/usr/share/fonts/X11/misc"
       FontPath     "/usr/share/fonts/X11/cyrillic"
       FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
       FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
       FontPath     "/usr/share/fonts/X11/Type1"
       FontPath     "/usr/share/fonts/X11/100dpi"
       FontPath     "/usr/share/fonts/X11/75dpi"
       FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
       Load  "GLcore"
       Load  "glx"
       Load  "record"
       Load  "dri"
       Load  "extmod"
       Load  "xtrap"
       Load  "dbe"
EndSection

Section "InputDevice"
       Identifier      "Generic Keyboard"
       Driver          "kbd"
       Option          "CoreKeyboard"
       Option          "XkbRules"      "xorg"
       Option          "XkbModel"      "pc105"
       Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "CorePointer"
       Option          "Device"        "/dev/input/mice"
       Option          "Protocol"      "ImPS/2"
       Option          "ZAxisMapping"  "4 5"
       Option          "Emulate3Buttons"       "true"
EndSection


Section "Monitor"
       #DisplaySize      310   230     # mm
       Identifier   "Monitor0"
       VendorName   "CPQ"
       ModelName    "COMPAQ MV700"
 ### Comment all HorizSync and VertRefresh values to use DDC:
       HorizSync    30.0 - 70.0
       VertRefresh  50.0 - 100.0
       Option      "DPMS"
EndSection

Section "Monitor"
       #DisplaySize      320   240     # mm
       Identifier   "Monitor1"
       VendorName   "EPI"
       ModelName    "7x0 Series"
 ### Comment all HorizSync and VertRefresh values to use DDC:
       HorizSync    30.0 - 72.0
       VertRefresh  50.0 - 160.0
       Option      "DPMS"
EndSection

Section "Device"
       ### Available Driver options are:-
       ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
       ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
       ### [arg]: arg optional
       #Option     "NoAccel"                   # [<bool>]
       #Option     "SWcursor"                  # [<bool>]
       #Option     "Dac6Bit"                   # [<bool>]
       #Option     "Dac8Bit"                   # [<bool>]
       #Option     "BusType"                   # [<str>]
       #Option     "CPPIOMode"                 # [<bool>]
       #Option     "CPusecTimeout"             # <i>
       #Option     "AGPMode"                   # <i>
       #Option     "AGPFastWrite"              # [<bool>]
       #Option     "AGPSize"                   # <i>
       #Option     "GARTSize"                  # <i>
       #Option     "RingSize"                  # <i>
       #Option     "BufferSize"                # <i>
       #Option     "EnableDepthMoves"          # [<bool>]
       #Option     "EnablePageFlip"            # [<bool>]
       #Option     "NoBackBuffer"              # [<bool>]
       #Option     "DMAForXv"                  # [<bool>]
       #Option     "FBTexPercent"              # <i>
       #Option     "DepthBits"                 # <i>
       #Option     "PCIAPERSize"               # <i>
       #Option     "AccelDFS"                  # [<bool>]
       #Option     "DDCMode"                   # [<bool>]
       #Option     "IgnoreEDID"                # [<bool>]
       #Option     "DisplayPriority"           # [<str>]
       #Option     "PanelSize"                 # [<str>]
       #Option     "ForceMinDotClock"          # <freq>
       #Option     "ColorTiling"               # [<bool>]
       #Option     "VideoKey"                  # <i>
       #Option     "RageTheatreCrystal"        # <i>
       #Option     "RageTheatreTunerPort"      # <i>
       #Option     "RageTheatreCompositePort"  # <i>
       #Option     "RageTheatreSVideoPort"     # <i>
       #Option     "TunerType"                 # <i>
       #Option     "RageTheatreMicrocPath"     # <str>
       #Option     "RageTheatreMicrocType"     # <str>
       #Option     "ScalerWidth"               # <i>
       #Option     "RenderAccel"               # [<bool>]
       #Option     "SubPixelOrder"             # [<str>]
       #Option     "ShowCache"                 # [<bool>]
       #Option     "DynamicClocks"             # [<bool>]
       #Option     "VGAAccess"                 # [<bool>]
       #Option     "ReverseDDC"                # [<bool>]
       #Option     "LVDSProbePLL"              # [<bool>]
       #Option     "AccelMethod"               # <str>
       #Option     "DRI"                       # [<bool>]
       #Option     "ConnectorTable"            # <str>
       #Option     "DefaultConnectorTable"     # [<bool>]
       #Option     "DefaultTMDSPLL"            # [<bool>]
       #Option     "LVDSBiosNativeMode"        # [<bool>]
       Identifier  "Card0"
       Driver      "ati"
       VendorName  "ATI Technologies Inc"
       BoardName   "Radeon RV100 QY [Radeon 7000/VE]"
       BusID       "PCI:1:0:0"
EndSection

Section "Device"
       ### Available Driver options are:-
       ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
       ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
       ### [arg]: arg optional
       #Option     "SWcursor"                  # [<bool>]
       #Option     "HWcursor"                  # [<bool>]
       #Option     "NoAccel"                   # [<bool>]
       #Option     "ShadowFB"                  # [<bool>]
       #Option     "UseFBDev"                  # [<bool>]
       #Option     "Rotate"                    # [<str>]
       #Option     "VideoKey"                  # <i>
       #Option     "FlatPanel"                 # [<bool>]
       #Option     "FPDither"                  # [<bool>]
       #Option     "CrtcNumber"                # <i>
       #Option     "FPScale"                   # [<bool>]
       #Option     "FPTweak"                   # <i>
       #Option     "DualHead"                  # [<bool>]
       Identifier  "Card1"
       Driver      "nv"
       VendorName  "nVidia Corporation"
       BoardName   "NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
       BusID       "PCI:2:14:0"
EndSection

Section "Screen"
       Identifier "Screen0"
       Device     "Card0"
       Monitor    "Monitor0"
       SubSection "Display"
               Viewport   0 0
               Depth     1
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     4
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     8
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     15
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     16
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     24
       EndSubSection
EndSection

Section "Screen"
       Identifier "Screen1"
       Device     "Card1"
       Monitor    "Monitor1"
       SubSection "Display"
               Viewport   0 0
               Depth     1
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     4
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     8
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     15
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     16
       EndSubSection
       SubSection "Display"
               Viewport   0 0
               Depth     24
       EndSubSection
EndSection
Section "ServerFlags"
 Option "Xinerama" "enable"
EndSection
```

---

### Post by jazzman14 on 2007-12-26
anyone?

---

### Post by tgalati4 on 2007-12-26
I have dual monitor set up with similar cards.  I would suggest changing the order of "Leftof" and "Rightof" displays or removing one of the position descriptions.  Perhaps this will fix the problem.

I'm not near my dual display setup to compare xorg.conf files, but it looks OK at first glance.  Although I vaguely remember having 2 mouse/cursor entries in my xorg.conf file.  I will have to boot my machine later today and compare.

Dual displays is generally a pain to set up, but once it is set up it works OK.

Edit:  I found my xorg.conf in a post from last year:

(This works on Dapper so Gutsy may behave differently.  Notice the dual entries for keyboard and mouse and only one position description.)


Section "ServerLayout"
Identifier "Terry's Custom Layout"
[B]Screen 0 "Screen0" 0 0
Screen 1 "Screen1" Below "Screen0"[/B]
[B]InputDevice "Generic Keyboard" "CoreKeyboard"
InputDevice "Configured Mouse" "CorePointer"[/B]
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
Option "xinerama" "on"
EndSection

Entire xorg.conf:

This works for me:

/etc/X11/xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier "Terry's Custom Layout"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" Below "Screen0"
InputDevice "Generic Keyboard" "CoreKeyboard"
InputDevice "Configured Mouse" "CorePointer"
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
Option "xinerama" "on"
EndSection

Section "Files"
RgbPath "/etc/X11/rgb
ModulePath "/usr/lib/xorg/modules"
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
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "dbe"
Load "record"
Load "xtrap"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
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

#Section "InputDevice"
# Driver "wacom"
# Identifier "stylus"
# Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
# Option "Type" "stylus"
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection

#Section "InputDevice"
# Driver "wacom"
# Identifier "eraser"
# Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
# Option "Type" "eraser"
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection

#Section "InputDevice"
# Driver "wacom"
# Identifier "cursor"
# Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
# Option "Type" "cursor"
# Option "ForceDevice" "ISDV4" # Tablet PC ONLY
#EndSection

Section "Device"
Identifier "Card0"
Driver "nv"
BusID "PCI:5:9:0" # from lspci 0000:05:09.0
EndSection

Section "Device"
Identifier "Card1"
Driver "i810"
BusID "PCI:0:2:0"
EndSection


Section "Monitor"
Identifier "Monitor1"
VendorName "PTS"
ModelName "Model 301"
Option "DPMS"
HorizSync 32-75
VertRefresh 60-75
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Nec"
ModelName "AccuSync 90 19 inch monitor"
Option "DPMS"
HorizSync 28-96
VertRefresh 43-160
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0" # Really long Intel card description
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "Screen1"
Device "Card1" # Really long nVidia card description
Monitor "Monitor1"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection

-----------------------------------------------

Substitute "Below" with "Leftof" or "Rightof". My monitors are set one on top of the other.

---

### Post by jazzman14 on 2007-12-26
Thank You So Much!
G-d Bless You

---

### Post by jazzman14 on 2007-12-26
okay i feel like a jerk but i have one more question:

well first of all i couldn't get xinerama working, it would crash X, but I'm okay with that.

my only little *issue* is that when i use the second display, the actual ubuntu screen is too large and when you move the mouse like towards the top, it drags up and shows the task bar, then when you move down it disappears, and as you move further down, you see the bottom taskbard...why is this happening?

(if i try to go to screen resolution or screens and graphics, X crashes too)

---

### Post by tgalati4 on 2007-12-26
Yes, I have experienced that wonky taskbar behavior as well.  There seems to be a 1-pixel threshhold and when you cross it the task bar moves in and out.  The way I solved it is to place one task bar on the top of one display and a panel at the bottom of the second display.  I have two monitors that are stacked so I have no taskbars or panels to interfere with the cursor crossing them between screens.

With side-by-side displays you could put a panel on the far left edge of one display and a taskbar on the far right edge of the second display.  This removes any bars when moving the mouse between them.

Yes, you lose the ability to change resolutions on the fly.  You need to settle on a decent resolution for both displays and lock them in.  You can do that by removing bogus resolutions in your xorg.conf.

What were the error messages in your .xsession-errors in your home directory?

I believe xinerama allows you to place a single application across both displays.  It's always worked for me so I don't know what the effect is if I turn it off.

Windows handles dual display in a much better fashion.

But then you are stuck with Windows and we don't want that.

Good luck.

---

### Post by jazzman14 on 2007-12-27
where can i edit the xorg.conf file to lock in my set resolution ( I want 1024 X 768). 

Also, I'm going to try to install compiz-fusion and see if that will make xinerama work?

---

### Post by jazzman14 on 2007-12-27
I guess my main question here is :

how can I lock the resolution in for both screens

and

how can i make the size of the right screen smaller, so that the image takes up the entire screen, instead of taking up a larger size?

---

### Post by tgalati4 on 2007-12-27
The newer xserver simplifies the xorg.conf file, but I think the old switches work.  Try removing unused resolution entries:

**From:**

SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

**To:**

SubSection "Display"
Depth 24
Modes  "1024x768"
EndSubSection
EndSection

To change the size of just one display, you may have to have two different resolutions.  My dual monitor setup has two different resolutions because the pitch (dot-size) is different between the two displays.

I don't believe compiz will effect xinerama, but I'm not sure if compiz will even work with dual display.  I haven't tried it yet.

---

