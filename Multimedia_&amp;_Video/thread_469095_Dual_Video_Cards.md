---
title: "Dual Video Cards"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by killjoy176 on 2007-06-09
Hi All.  OK.  I got Feisty installed rock solid with an NVIDIA 8800GTX, Beryl and whatnot.  I configured the xorg.conf for TwinView so i have two monitors working beautifully.  My problem is I have a second 8600 GT installed with a third monitor and no matter what I try, Ubuntu doesn't see it.  When i go into NVIDIA Settings, all I see is the 8800GTX.  I manually edited Xorg.conf to included the 8600 GT with the proper PCI address and still nada.  Can someone review my Xconf and tell me what the hell I am missing?  :D  I'm so close and really want to switch from Vista, but three monitors are a must and I have to be able to move any window to any screen easily.  If it breaks Beryl, I can fight with that later.  Thanks!

Section "ServerFlags"
    Option         "Xinerama" "true"
EndSection

#Section "ServerLayout"
 #   Identifier     "Default Layout"
 #  Screen         "Main Screen" 0 0
 # InputDevice    "Generic Keyboard"
 # InputDevice    "Configured Mouse"
#EndSection

Section "ServerLayout"
    Identifier     "Triple Head"
    Screen         "Main Screen"
    Screen         "Third Screen" LeftOf "Main Screen"
    Screen         "Fourth Screen" LeftOf "Third Screen"
    Option         "Xinerama"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
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
    Load           "dbe"
EndSection

#################################INPUTDEVICES###############################

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

##############################MONITORS#######################################

Section "Monitor"
    Identifier     "Main Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Second Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Third Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier      "Fourth Monitor"
    HorizSync        28.0 - 51.0
    VertRefresh      43.0 - 60.0
    Option          "DPMS"
EndSection

############################GRAPHICSCARDS#####################################

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTX] 0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTX] 1"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

#######################

Section "Device"
    Identifier     "nVidia Corporation G84 [GeForce 8600 GT] 0"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    BusID          "PCI:9:0:0"
    Screen          3
EndSection

Section "Device"
    Identifier     "nVidia Corporation G84 [GeForce 8600 GT] 1"
    Driver         "nvidia"
    BusID          "PCI:9:0:0
    Screen          4
EndSection

####################################SCREENS####################################

Section "Screen"
    Identifier     "Main Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTX] 0"
    Monitor        "Main Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Second Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTX] 1"
    Monitor        "Second Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Third Screen"
    Device         "nVidia Corporation G84 [Geforce 8600 GT] 0"
    Monitor        "Third Monitor"
    DefaultDepth    24
    SubSection     "Display"
       Depth        24
       Modes       "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Fourth Screen" 
    Device         "nVidia Corporation G84 [GeForce 8600 GT] 1"
    Monitor        "Fourth Monitor"
    DefaultDepth    24
    SubSection     "Display"
       Depth        24
       Modes       "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by killjoy176 on 2007-06-11
Nobody?  Seriously?

---

### Post by Azakus on 2007-06-11
You have to get the new **BETA** nvidia drivers and install a recompiles nvidia-kernel module.
Easy to do with the envy program:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by spivee69 on 2007-06-19
I'm not sure what you can do with your xorg.conf, I've been playing with a similar setup myself.  I have two 7600GTs and am running three screens.  I can get TwinView and Beryl working fine on two monitors, and I can get all three monitors working (but no beryl).  

I got a lot out of reading this page [http://pwp.netcabo.pt/0150048402/linux/Multiple_Nvidia_Multiple_Head.html]("http://pwp.netcabo.pt/0150048402/linux/Multiple_Nvidia_Multiple_Head.html")
as well as reading through the [README]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7667/README.txt")

Maybe this will help.  Here's a copy of my current xorg.conf (the important sections anyway).  This allows three screens to be used as one large desktop.  My config is quite a bit different than yours.  I put the TwinView settings in the Device sections (yours are in the screen sections) and I only have two devices configured, one per physical card, whereas you seem to have four devices configured, I'm assuming one device per connection port.  

```

########################################################
#  Screens Section for TwinView
########################################################

Section "Monitor"
    Identifier     "Sceptre"
    ModelName      "X22WG-Gamer"
    DisplaySize     380    305
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Fuji"
    ModelName      "FP-988D"
    DisplaySize     474    296
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Samsung"
    ModelName      "SyncMaster 226BW"
    DisplaySize     474    296
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

########################################################
#  Devices Section - One per Dual Head Card
########################################################

Section "Device"
    Identifier     "GPU-0"
    Driver         "nvidia"
    VendorName     "EVGA"
    BoardName      "7600GT" 
    Option         "RenderAccel"   "True"
    Option         "TwinView"
    Option         "TwinViewOrientation"   "RightOf"
    Option         "MetaModes"             "1680x1050, 1680x1050"
    Option         "ConnectedMonitor"      "DFP-0"
    Option         "UseEdidFreqs"          "True" 
    BusID          "PCI:2:0:0"
EndSection

Section "Device"
    Identifier     "GPU-1"
    Driver         "nvidia"
    VendorName     "EVGA"
    BoardName      "7600GT"
    Option         "RenderAccel"           "True"
    Option         "TwinView"
    Option         "TwinViewOrientation"   "LeftOf" 
    Option         "MetaModes"             "1680x1050, 1280x1024"
    Option         "ConnectedMonitor"      "CRT-0, DFP-0"
    Option         "UseEdidFreqs"          "True"
    BusID          "PCI:7:0:0"
EndSection

########################################################
#  Screens Section for TwinView
########################################################

Section "Screen"
    Identifier     "Center"
    Device         "GPU-0"
    Monitor        "Sceptre"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Right"
    Device         "GPU-0"
    Monitor        "Fuji"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Left"
    Device         "GPU-1"
    Monitor        "Samsung"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

##################################
# Layout Section
##################################

Section "ServerLayout"
    Option         "Xinerama"
    Identifier     "Default Layout"
    Screen         0 "Center" 0 0  
    Screen         1 "Right" LeftOf "Center"
    Screen         2 "Left" LeftOf "Right"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

```

---

### Post by broncavfan on 2007-06-30
I'm not sure if this helps exactly, but I was able to get three screens working with two video cards.  I have an nVidia 6100 onboard with a flat screen 1280x1024 and and nVidia 5200FX PCI with two "box" monitors 1024x768.  I have them setup in a triangular shape with the flat screen on top of the two "chunkys", mostly because I need to get a bigger desk.  I have  TwinView working on the bottom 2 monitors with beryl running just fine and the top screen is a seperate x screen with MetaCity running smoothly.  I don't really see a need to have beryl working on all three monitors with this setup, so I'm content with the top screen not running it (for now, maybe I'll try to figure it out).

Anyway, in order to get this working I first made sure my BIOS was loading the onboard video card first.  I'm not sure why this worked, but when I had the PCI card loading first I was having strange black screen problems.  Obviously, all my software is up to date.  Unfortunately the nvidia-settings didn't help much because of the triangular shape that I was trying to achieve.  Here's my xorg.conf that got this working:

```

    Section "ServerLayout"
    Identifier     "Layout0"
    Screen         "Screen0" 0 1024  ##bottom screens 0 over, 1024 down
    Screen         "Screen1" 512 0   ##top screen 512 over, 0 down
    ##if you move a screen outside of the reach of the mouse, you won't be able to get to it
    ##for example, if I change 1024 to 1030 I won't be able to reach the top screen because
    ##the top screen ends at 1024 down and the bottom screen would start at 1030 down
    ##maybe if you changed the mouse properties so you'd be able to be able to leave the 
    ##top of the screen???
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "int10"
    Load           "type1"
    Load           "i2c"
    Load           "dbe"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "vbe"
EndSection

##Probably don't need this Section
Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Compaq MV540"
    HorizSync       30.0 - 54.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "COMPAQ MV540"
    HorizSync       30.0 - 54.0
    VertRefresh     50.0 - 120.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA712-2SERIES"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    Option         "RenderAccel" "True"
    BusID          "PCI:3:8:0"
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6100"
    Option         "RenderAccel" "True"
    BusID          "PCI:0:5:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "metamodes" "1024x768, 1024x768"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "metamodes" "1280x1024"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection


Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

(I know, I'm probably missing some things and it could probably use a cleanup, I'm still just figuring this out)

Then, in System->Prefences->Sessions->Startup Programs I added the line
```

beryl --screen :0.0

```
and named it something like "Beryl on Bottom".  I don't really use my computer for games, so this might not be the best solution for people worried about which graphics card they're playing games on.  I think with a little more configuring you could move the top monitor between the bottom two and still have beryl working on those two.  Like I said, I didn't want beryl running on the top screen anyway.  I mean, seriously, is 10 desktops not enough (1 x 2 screens x 4 desktops on cube + 2 desktops on top)?  It is for me.  After reading other posts, I think it would also be possible to get beryl working on the top monitor seperately if I setup a different x session for it.  Something like that, I still need to do more research and tinkering.

I hope this helps killjoy, or at least somebody out there.  I'll keep you updated...

---

### Post by spivee69 on 2007-07-02
Thanks broncavfan!  I'll definitely give this a try.  I hadn't even considered trying to get beryl to work on only a couple of the monitors instead of all three.

BTW, if you run a screen saver, does it spread across all three monitors or does it run seperately?

---

