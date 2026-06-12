---
title: "DVI to HDMI, setup multiple displays - NVIDIA card doesn't detect any HDMI signal"
date: 2009-01-21
forum: Multimedia Software
---

### Post by Chris81 on 2009-01-21
Hello guys, I will highly appreciate your assistance.
I am sure that there are many topics about this but I think I have read most of them and didn't find the solution to my problem.

Recently I have purchased a new Sharp AQUOS LCD 32'' (HD ready, 2 HDMI ports etc.). I have NVIDIA GeForce 9500GT 512RAM (it has VGA, DVI and S-Video output), the current driver is 181.20 (I think the latest). In order to connect the PC with the TV I have purchased a 5m cable DVI-HDMI. The first time I connected the PC and the TV, I started the NVIDIA TV Wizard / Display Wizard - it has detected the HDMI and asked for resolution..., everything went smooth and I have successfully setup a Dualview and Clone modes (I was able to set the HDMI format to 1080i).

Couple of days later, I started the PC and I noticed that my mouse doesn't move out of the primary display. I started the TV to the correct input and there was no signal, when I went to the NVIDIA Control Panel the Sharp TV was not listed. This was very strange and I started testing different settings, resolutions, rebooting, changing the HDMI port etc. Once I changed the HDMI port, I was able to run new Display Wizard which asked me for the HDMI format and it was ok (after numerous tests). Then I tried changing to the first HDMI port and everything was fine for another couple of days.

Now I had to make some house arrangements and I had to disconnect the TV. When I connected everything as it was there was no signal.
I tried running the wizard once again without any success. It seems that now the NVIDIA is not receiving any signal from the TV, there is no Sharp TV recognized and the only thing I can see when I try to setup multiple displays is simply TV. The Television Setup Wizard says that this is TV, Connector type: Auto-select, Signal type: M/NTSC

I can no longer detect the HDMI signal (on both HDMI ports) and I don't have any ideas how and why this has happened - it was working fine!!!

Does anyone had such issue and is there any solution to this? Is the problem with NVIDIA dirvers or something else? I will be glad to receive suggestions and some basic step-by-step guide to fix this problem.

Thanks,
Chris

---

### Post by Lord C on 2009-03-08
Also having a similar problem.

HDMI was working fine for months. I have two monitors connected via DVI, and the TV connected through HDMI (Nvidia GeForce 9800 GX2).

Each display had it's own X session, because Xinerama is nasty and laggy.

Since a couple of weeks ago, my PC has no longer been picking up the HDMI connection, for some reason.

Upon loading nvidia-settings, I see the following errors in console;

```
$ sudo nvidia-settings 

ERROR: Cannot open display 'cosmos:0.0'.


ERROR: Cannot open display 'cosmos:0.1'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 23 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 24 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 25 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 26 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 27 of configuration
       file '/home/lordc/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 28 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 29 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 30 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 31 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 32 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 33 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 34 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 35 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 36 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 37 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 38 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 39 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 40 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 41 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 42 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 43 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 44 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 45 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 46 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 47 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 48 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 49 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 50
       of configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 51 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 52 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 53
       of configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       54 of configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 55 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 56 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 57 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 58 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 59 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 60 of configuration
       file '/home/lordc/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 61 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 62 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 63 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 64 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 65 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 66 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 67 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 68 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 69 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 70 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 71 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 72 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 73 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 74 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 75 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 76 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 77 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 78 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 79 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 80 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 81 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 82 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 83
       of configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line 84 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 85 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 86
       of configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       87 of configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 88 of
       configuration file '/home/lordc/.nvidia-settings-rc' (no Display
       connection).

```

Here's my Xorg.conf

```
#

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

#Section "Files"
#    RgbPath         "/usr/X11R6/lib/X11/rgb"
#EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load 	   "dbe"
EndSection

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

#----------------Monitors----------------#
################# Video7 ################# 
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "CMO CMC 22 W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

#################  HDTV  ################# 
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSP YT08H"
    Modeline "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
    HorizSync 	   47.712
    VertRefresh    60.015
EndSection

#################  Dell  ################# 
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 1908FP"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

#----------------Devices-----------------#
################# Video7 ################# 
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "G92-450"
    BusID          "PCI:6:0:0"
    Screen          0
EndSection

#################  HDTV  ################# 
Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "G92-450"
    BusID          "PCI:6:0:0"
    Screen          1
EndSection

#################  Dell  ################# 
Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "G92-450"
    BusID          "PCI:5:0:0"
EndSection

#----------------Screens-----------------#
################# Video7 ################# 
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

#################  HDTV  ################# 
Section "Screen"
    Identifier     "Screen2"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
#    Option         "metamodes" "DFP-0: 1280x768_60.00 +0+0"
#    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
#    Option "FlatPanelProperties" "scaling = centered"
#    Option "ModeValidation" "DFP-0: NoEDIDModes"

    Option         	"AllowGLXWithComposite" "True"
    Option         	"AddARGBGLXVisuals" "True"

    Option         "DPMS"
    Option	   "UseEDID" "False"
    Option	   "UseEDIDFreqs" "FALSE"
    Option	   "UseEDIDDpi" "FALSE"
#    Option	   "ModeValidation" "DFP-0: NoEDIDModes, NoMaxPClkCheck, NoHorizSyncCheck, NoVertRefreshCheck"
    
    Option         "metamodes" "1280x768_60.00 +0+0"

#    Option 	   "CustomEDID" "DFP-0:/home/lordc/Scripts/edid.bin"

    SubSection     "Display"
        Depth       24
#	Modes 	    "nvidia-auto-select"
	Modes	    "1280x768_60.00"
    EndSubSection
EndSection

#################  Dell  ################# 
Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard2"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I'm running Ubuntu 8.10 (32bit).

Just updated nvidia drivers, still no look. Might try downgrading them. Tried different HDMI cables and such. This is an odd problem.

---

### Post by 4dplane on 2009-03-13
Any luck with this problem?

---

### Post by inobe on 2009-03-13
i don't think that is backwards compatible !

hdmi to dvi "yes" but not the other way around.......

i too have had bad results from a windows platform

edit: the adapter should specify it's direction' there are dvi to hdmi adapters' but there are also hdmi to dvi adapters as well

---

### Post by Lost_in_Edmonton on 2009-12-24
Mine is working with 185.18.36 on Ubuntu Linux-x86_64, well except sound through the HDMI. 

Here is a copy of my xorg.conf

xxxxx@xxxxx-desktop:~$ cat /etc/X11/xorg.conf
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
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
    VendorName     "SAMSUNG"
    ModelName      "Samsung SyncMaster 226BW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "SAMSUNG"
    ModelName      "SAMSUNG LN52B530"
    HorizSync       26.0 - 68.0
    VertRefresh     24.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "SAMSUNG"
    ModelName      "Samsung SyncMaster 226BW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GX2"
    BusID          "PCI:5:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GX2"
    BusID          "PCI:5:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GX2"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1920x1080_60 +0+0"
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
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

xxxxx@xxxx-desktop:~$

---

