---
title: "Nvidia tearing"
date: 2009-10-20
forum: Mythbuntu
---

### Post by jonnybignote on 2009-10-20
Hi all

running mythbuntu 9.04 on Nvidia 8400 gs.  Can't get rid of tearing  - halfway down screen or so.  Just wondered if anyone had found an Nvidia driver that gets rid of on 0.21 (I assume it will go away in 0.22 but in the meantime...).  I have tried other drivers but for now am back on 180.44 as it seems to make little difference.  I have also tried the various V-blank options in Nvidia settings.  

Does everyone using this card or others have this problem?  It's very distracting now in movement scenes - I find that I'm very sensitive to it...driving me nuts.

Any advice appreciated

---

### Post by williammanda on 2009-10-20
I'm using 180.60 with a 9600GT without any tearing. You might want to post your xorg.conf and your nvidia x server settings.

---

### Post by jonnybignote on 2009-10-21
Great - thanks for replying.  Here is the xorg - This was generated and I haven't done anything to it - same for X-server settings

xorg.conf

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SAMSUNG"
    HorizSync       30.0 - 49.0
    VertRefresh     59.0 - 71.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    Option         "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x720_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


**************

Nvidia-settings

# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Tue Oct 20 13:46:44 2009
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = No
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

0/CursorShadow=0
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/SyncToVBlank=1
0/LogAniso=0
0/FSAA=1
0/TextureSharpen=0
0/AllowFlipping=0
0/FSAAAppControlled=0
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=1
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/DigitalVibrance[DFP-0]=0
0/GPUScaling[DFP-0]=65538
0/XVideoTextureBrightness=0
0/XVideoTextureContrast=0
0/XVideoTextureHue=10
0/XVideoTextureSaturation=0
0/XVideoTextureSyncToVBlank=1
0/XVideoSyncToDisplay=65536

If you see nothing amiss here, maybe I'll try for the 180.60 - do you have a good way of removing the current driver (other than removing via hardware drivers or synaptic) as I've had trouble removing the previous drivers which took a while.

Thanks again

---

### Post by williammanda on 2009-10-21
Try changing based on the attached photos.
I will try to look up changing nvidia driver.

---

### Post by williammanda on 2009-10-21
This doesn't look bad.

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+change]("http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+change")

---

### Post by yonkiman on 2009-10-21
This fixed it for me (I was using component video out, not sure if it will work with other video modes or the latest drivers):

[http://ubuntuforums.org/showthread.php?t=872130](http://ubuntuforums.org/showthread.php?t=872130)

---

### Post by jonnybignote on 2009-10-21
Thanks guys for the help.  Yes - it was the disabling composite thing.  It's not supposed to be an issue beyond 185 but I tried it anyway in 185 and it crashed X.  At the time I just thought it non supported - though now I realize I must have typed it in wrong :mad: .  I tried disabling composite with the 190 drivers and the tearing goes away!  Now I just need to find out the best driver for lower CPU usage as its quite high - going back to 180 and see where I get to from there.

Happy at least knowing tearing won't be an issue.  Thanks guys and sorry I didn't follow the crumbs properly in the first place!

Jonathan

---

