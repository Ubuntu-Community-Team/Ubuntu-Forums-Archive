---
title: "xorg.config"
date: 2010-08-02
forum: Multimedia Software
---

### Post by wrench 36 on 2010-08-02
I have just updated to 10.04 from 9.04. I am having trouble with the configuration of xorg.conf file. my video card is a nvidia GeForce 9400 GT, and i am pretty shure that the svideo is not the default setting (the video card came with an svideo cable that had 3rca ends that r 4 an HD tv.  the svideo to tv (composet)is what i would like to use as my  primary display (on an old tv). with my current xorg.conf file i start my pc up with both vga and svideo hooked up and i only get the bios startup on the vga, the tv is blank. then and underscore flashes in the upper left of the vga monitor, then a flash of the nvidi logo and the login screen appear on both vga monitor and the tv, but only the vga monitor has the login box. i log in and then i have separate x screens. Just like with ubuntu 9.04. if i dont have my vga connected to the video card the tv starts with the bios screen and the under score in the upper left then goes blank just befor the login(know that is just with the svideo to the tv plugged in to the video card nothin else) so at this point im at a blank screen. i hit enter and enter my password, i here the loginsound on my stero but still no picture on the tv. i have to ctrl-alt-backspace (after i enabled it) and plugin the vga to make it work on the tv. 
how then can i make the tv as the only display, without the vga monitor hooked up?
and possibly hook the vga up simultaneously sometimes.
do i need to modify the /home/user/.nvidia-settings-rc or the xorg.conf?
before i upgraded to 10.04 i only used the svideo to tv.
i have modified the xorg.conf file so that i could get the svideo to work, but i just want the one monitor.
i have even tried ctrl-alt-and th f keys it just makes the underscore flash in the upperleft corner of the screen

these r the links i used to get svideo to work
[http://en.wikibooks.org/wiki/NVidia/TV-OUT](http://en.wikibooks.org/wiki/NVidia/TV-OUT)
[http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html)
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)


here is a coppy of my xor confi file and under that is the /home/user/.nvidia-settings-rc

Section "ServerLayout"

# Removed Option "Xinerama" "0"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SCEPTRE D73F"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"
    Option         "ConnectedMonitor" "Monitor[1]"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #adjust using 'lspci' or cat /proc/pci
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"
    Option         "ConnectedMonitor" "Monitor[1]"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


-----------------------------------------------------------------------------------------------
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Mon Aug  2 16:36:17 2010
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
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
0/SyncToVBlank=0
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/DigitalVibrance[CRT-1]=0
0/OverscanCompensation[CRT-1]=0
0/XVideoTextureBrightness=0
0/XVideoTextureContrast=0
0/XVideoTextureHue=0
0/XVideoTextureSaturation=0
0/XVideoTextureSyncToVBlank=1
0/XVideoSyncToDisplay=2
1/CursorShadow=0
1/CursorShadowAlpha=64
1/CursorShadowRed=0
1/CursorShadowGreen=0
1/CursorShadowBlue=0
1/CursorShadowXOffset=4
1/CursorShadowYOffset=2
1/SyncToVBlank=0
1/LogAniso=0
1/FSAA=0
1/TextureSharpen=0
1/AllowFlipping=1
1/FSAAAppControlled=1
1/LogAnisoAppControlled=1
1/OpenGLImageSettings=1
1/FSAAAppEnhanced=0
1/RedBrightness=0.000000
1/GreenBrightness=0.000000
1/BlueBrightness=0.000000
1/RedContrast=0.000000
1/GreenContrast=0.000000
1/BlueContrast=0.000000
1/RedGamma=1.000000
1/GreenGamma=1.000000
1/BlueGamma=1.000000
1/DigitalVibrance[TV-0]=0
1/ImageSharpening[TV-0]=127
1/OverscanCompensation[TV-0]=0
1/XVideoTextureBrightness=0
1/XVideoTextureContrast=0
1/XVideoTextureHue=0
1/XVideoTextureSaturation=0
1/XVideoTextureSyncToVBlank=1
1/XVideoSyncToDisplay=256

---

### Post by wrench 36 on 2010-08-03
i cant find a thing on making the tv ur primary monitor
has any one set up the tv as the primary monitor?

---

### Post by realzippy on 2010-08-03
Edit:
So you want your Monitor/TV setup back you had before upgrading?Is this the problem ?
If so,checking/reinstalling the nvidia driver and then copying your working xorg.conf backup (from 9.04) should do it.

---

### Post by wrench 36 on 2010-08-03
as far as using any thing from the prevous 9.04. i have always zeroed the drive for a fresh install, and started, and or upgraded as i went.  my fault. huu
when i set the 9.04 up it was the same hardware setup as the 10.04. so after i figured out how to save the xorg.conf threw the gui, as per  "gksudo nvidia-settings".it worked in seperate x (vga and svideo) two main screens.  EXAMPLE when i started the pc, both screens worked exactly the same (ie both screens showed bios, ubuntu start up page, and both screens have login)
with all that said basically i just unplugged the vga output and the tv still worked. 

But now for some reason on the new 10.04 version when i got to this point, with the vga unpluged on startup, the tv showes bios, ubuntu startup screen, then blanks. 

I can hit enter at this point and login, i here the startup sound but still no screen.

---

### Post by realzippy on 2010-08-04
Sorry I do not get it.

Do you have a copy of the old xorg.conf running or don`t you?

---

### Post by wrench 36 on 2010-08-04
no i wiped the drive. (killdisk)

---

