---
title: "resolution problem"
date: 2010-02-14
forum: Multimedia Software
---

### Post by Jithin Sunny on 2010-02-14
[COLOR=Red]**please help me to get 1024 X 768 resolution  in ubuntu 9.1 desktop edition...please...**[/COLOR]

my xorg.conf.new says..,



Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dri"
    Load  "glx"
    Load  "extmod"
    Load  "dri2"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "Accel"                  # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "TurboQueue"             # [<bool>]
        #Option     "FastVram"               # [<bool>]
        #Option     "HostBus"                # [<bool>]
        #Option     "RenderAcceleration"     # [<bool>]
        #Option     "ForceCRT1Type"          # <str>
        #Option     "ForceCRT2Type"          # <str>
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "Vesa"                   # [<bool>]
        #Option     "MaxXFBMem"              # <i>
        #Option     "EnableSiSCtrl"          # [<bool>]
        #Option     "SWCursor"               # [<bool>]
        #Option     "HWCursor"               # [<bool>]
        #Option     "UseColorHWCursor"       # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "Reflect"                # <str>
        #Option     "Xvideo"                 # [<bool>]
        #Option     "InternalModes"          # [<bool>]
        #Option     "OverruleFrequencyRanges"     # [<bool>]
        #Option     "RestoreBySetMode"       # [<bool>]
        #Option     "ForceCRT1"              # [<bool>]
        #Option     "XvOnCRT2"               # [<bool>]
        #Option     "PanelDelayCompensation"     # <i>
        #Option     "PDC"                    # <i>
        #Option     "PanelDelayCompensation2"     # <i>
        #Option     "PDC2"                   # <i>
        #Option     "PanelDelayCompensation1"     # <i>
        #Option     "PDC1"                   # <i>
        #Option     "EMI"                    # <i>
        #Option     "LVDSHL"                 # <i>
        #Option     "ForcePanelRGB"          # <i>
        #Option     "SpecialTiming"          # <str>
        #Option     "TVStandard"             # <str>
        #Option     "UseROMData"             # [<bool>]
        #Option     "UseOEMData"             # [<bool>]
        #Option     "YV12"                   # [<bool>]
        #Option     "CHTVType"               # [<bool>]
        #Option     "CHTVOverscan"           # [<bool>]
        #Option     "CHTVSuperOverscan"      # [<bool>]
        #Option     "CHTVLumaBandwidthCVBS"     # <i>
        #Option     "CHTVLumaBandwidthSVIDEO"     # <i>
        #Option     "CHTVLumaFlickerFilter"     # <i>
        #Option     "CHTVChromaBandwidth"     # <i>
        #Option     "CHTVChromaFlickerFilter"     # <i>
        #Option     "CHTVCVBSColor"          # [<bool>]
        #Option     "CHTVTextEnhance"        # <i>
        #Option     "CHTVContrast"           # <i>
        #Option     "SISTVEdgeEnhance"       # <i>
        #Option     "SISTVAntiFlicker"       # <str>
        #Option     "SISTVSaturation"        # <i>
        #Option     "SISTVCFilter"           # [<bool>]
        #Option     "SISTVYFilter"           # <i>
        #Option     "SISTVColorCalibFine"     # <i>
        #Option     "SISTVColorCalibCoarse"     # <i>
        #Option     "SISTVXScale"            # <i>
        #Option     "SISTVYScale"            # <i>
        #Option     "TVXPosOffset"           # <i>
        #Option     "TVYPosOffset"           # <i>
        #Option     "SIS6326TVAntiFlicker"     # <str>
        #Option     "SIS6326TVEnableYFilter"     # [<bool>]
        #Option     "SIS6326TVYFilterStrong"     # [<bool>]
        #Option     "SIS6326TVForcePlug"     # <str>
        #Option     "SIS6326FSCAdjust"       # <i>
        #Option     "YPbPrAspectRatio"       # <str>
        #Option     "TVBlueWorkAround"       # [<bool>]
        #Option     "ColorHWCursorBlending"     # [<bool>]
        #Option     "ColorHWCursorBlendThreshold"     # <i>
        #Option     "CRT2Detection"          # [<bool>]
        #Option     "ForceCRT2ReDetection"     # [<bool>]
        #Option     "SenseYPbPr"             # [<bool>]
        #Option     "CRT1Gamma"              # [<bool>]
        #Option     "CRT2Gamma"              # [<str>]
        #Option     "GammaBrightness"        # <str>
        #Option     "GammaBrightnessCRT2"     # <str>
        #Option     "CRT2GammaBrightness"     # <str>
        #Option     "Brightness"             # <str>
        #Option     "NewGammaBrightness"     # <str>
        #Option     "CRT2Brightness"         # <str>
        #Option     "CRT2NewGammaBrightness"     # <str>
        #Option     "Contrast"               # <str>
        #Option     "NewGammaContrast"       # <str>
        #Option     "CRT2Contrast"           # <str>
        #Option     "CRT2NewGammaContrast"     # <str>
        #Option     "CRT1Saturation"         # <i>
        #Option     "XvGamma"                # [<str>]
        #Option     "XvDefaultContrast"      # <i>
        #Option     "XvDefaultBrightness"     # <i>
        #Option     "XvDefaultHue"           # <i>
        #Option     "XvDefaultSaturation"     # <i>
        #Option     "XvDefaultDisableGfx"     # [<bool>]
        #Option     "XvDefaultDisableGfxLR"     # [<bool>]
        #Option     "XvChromaMin"            # <i>
        #Option     "XvChromaMax"            # <i>
        #Option     "XvUseChromaKey"         # [<bool>]
        #Option     "XvInsideChromaKey"      # [<bool>]
        #Option     "XvYUVChromaKey"         # [<bool>]
        #Option     "XvDisableColorKey"      # [<bool>]
        #Option     "XvUseMemcpy"            # [<bool>]
        #Option     "BenchmarkMemcpy"        # [<bool>]
        #Option     "UseSSE"                 # [<bool>]
        #Option     "XvDefaultAdaptor"       # <str>
        #Option     "ScaleLCD"               # [<bool>]
        #Option     "CenterLCD"              # [<bool>]
        #Option     "EnableHotkey"           # [<bool>]
        #Option     "ForceCRT1VGAAspect"     # <str>
        #Option     "ForceCRT2VGAAspect"     # <str>
        #Option     "MergedFB"               # [<str>]
        #Option     "TwinView"               # [<str>]
        #Option     "MergedFBAuto"           # [<bool>]
        #Option     "CRT2HSync"              # <str>
        #Option     "SecondMonitorHorizSync"     # <str>
        #Option     "CRT2VRefresh"           # <str>
        #Option     "SecondMonitorVertRefresh"     # <str>
        #Option     "CRT2Position"           # <str>
        #Option     "TwinViewOrientation"     # <str>
        #Option     "MetaModes"              # <str>
        #Option     "MergedDPI"              # <str>
        #Option     "MergedXinerama"         # [<bool>]
        #Option     "TwinviewXineramaInfo"     # [<bool>]
        #Option     "MergedXineramaCRT2IsScreen0"     # [<bool>]
        #Option     "MergedNonRectangular"     # [<bool>]
        #Option     "MergedMouseRestriction"     # [<bool>]
    Identifier  "Card0"
    Driver      "sis"
    VendorName  "Silicon Integrated Systems [SiS]"
    BoardName   "661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
    BusID       "PCI:1:0:0"
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
,


please help me to get 1024X768 resolution please.....

---

### Post by Jithin Sunny on 2010-02-15
please pay attention to my problem....please....

---

### Post by xc3RnbFO8P on 2010-02-15
Show the output of:
> sudo lshw -C display
> lsmod | grep sis

---

### Post by Jithin Sunny on 2010-02-16
> **Ringi said:**
> Show the output of:


output of sudo lshw -C display :

*-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff(prefetchable) memory:feae0000-feafffff ioport:bc00(size=128)

output of lsmod | grep sis :

sis190                 17824  0 
mii                     5212  1 sis190
sis_agp                 6972  0 
agpgart                34988  2 sis_agp,amd64_agp

---

### Post by xc3RnbFO8P on 2010-02-16
> sudo gedit /etc/X11/xorg.conf
Change this:
> Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection
to:
> Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
 DefaultDepth 24
 SubSection "Display"
  Depth 8
  Modes "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 16
  Modes "1024x768" "800x600" "640x480"
 EndSubSection
 SubSection "Display"
  Depth 24
  Modes "1024x768" "800x600" "640x480"
 EndSubSection
EndSection

---

### Post by Jithin Sunny on 2010-02-22
I did that...but its not working..resolution changed to 800 X 600.but not showing 1024 X 768 resolution in display option menu.

---

### Post by Mayfairy on 2010-02-22
Found this thread via google when searching for suitable drivers for our old Acer computer we just installed the 9.10 Karmic on top of old 8.04. 

The restricted drivers the system offers are installed ok but the resolution (which by default is 800x600) are taken down to 640x480 with an option to use 480x320 as well which isn't desired as we're trying to get the 1024x768 back. 

It's been a long time since I installed the 8.04 system (duh, April 2008) and I can't remember for sure what drivers we had installed back then.

Anyways, the restricted drivers didn't work so we removed them. I just downloaded the drivers from Nvidia's site and was gonna install them but little missus decided to call it a night and shut down the computer.

So, if you care to wait til tomorrow for the info if it works or not then feel free to do so. I'll post the info as soon as I know if it works. 

Also you could go to the Nvidia.com and choose download drivers. 
It'll ask you a few questions that you should answer: 
1) Geforce
2) Geforce 4 MX series
3) Linux 32-bit (or 64-bit if that's your style)
4) Your preferred language here. 
And click Search. It'll return you one set of drivers that you should download. On the next page where you will see a lot of legal blahblah instead of hitting Accept you should right click and Save file as cause otherwise you'll be looking at an impressive amount of text on your screen. 
After saving the file (named NVIDIA-Linux-x86-100.14.11.pkg1.run) on your Desktop or wherever you want you should open up a terminal and execute a command "sh NVIDI<tab>" (you could write the whole name or autocomplete with Tab button. 
Before doing that you're supposed to kill your X session by typing "sudo gdm stop" or whatever means you think are suited for you. Beware however, this will take away your desktop. Hit Ctrl-Alt-F1 to go to the dreaded black screen where you will enter your login details, then move to the right directory via 'cd' command and execute the "sh NVIDIA<tab>" command. 
By agreeing on everything the installer then asks you should get the drivers installed. After the installer is done you're just a reboot away from your new shiny desktop with 1024x800 resolution. 

I'm pretty sure those are the drivers we used in the past to get the higher resolutions working, but I can't be 100% sure. It might very well trash your settings so that you can't enter your desktop and then you'd have no way of finding the cure for that. 

Anyways, if you're willing to try then feel free to do so.

---

### Post by Mayfairy on 2010-02-23
A little update on things. It seems the Nvidia drivers are not to blame. Ended up installing the 96 restricted drivers  (those with 640x480 resolution) and the real culprit is the monitor that's not being identified correctly. 
Still trying to figure out what to do.

---

### Post by Mayfairy on 2010-02-23
All day gone with some fiddling. 

In the end what worked for me was to install the restricted drivers Ubuntu keeps suggesting (version 96 for me) even though the resolution goes down. 

Then boot up with recovery mode and run "nvidia-xconfig" to create new xorg.conf file. First make sure you have deleted your old one out of the way. 
NOTE: On recovery mode I was able to do "startx" to get a working desktop. "gdm" didn't work, just "startx".

After nvidia-xconfig creates the xorg.conf for you go and edit it with nano and change the VertRefresh and HorizSync values to those of your monitor (which you have googled beforehand). Also make sure your file has the following lines:

Section "Extensions"
Option "Composite" "Disable"
EndSection

And the most important thing; wherever there is the line with all the display modes be sure to delete the resolutions that are higher than what your monitor is capable of. I struggled for hours with this part and only by accident I removed the bigger resolutions. 

Also make sure that if you have nvidia card your driver section reads "nvidia" instead of "nv". 

That should be it. Boot up and enjoy. 

This seems to be a common problem with Acer AL1916 monitors throughout the Ubuntu lifespan. 

My case is closed now and I'm hoping that the original poster comes back to read this and gets his machine working.

---

