---
title: "Bad video output on secondary screen"
date: 2010-04-30
forum: Multimedia Software
---

### Post by gangeli on 2010-04-30
I upgraded to Ubuntu 10.04 from 9.10 on my laptop and my VGA screen suffers from what appears to be maybe a refresh rate problem? At native resolution, vertical "squiggly lines" move downward on the monitor, larger on the edges and becoming clear by the middle. At lower resolutions, the distortion becomes more violent, and at the lowest resolutions, I get an "Out of Range" exception on the monitor (i.e. 800x600 I get "out of range -- horizontal frequency 27.9, vertical frequency: 44.6). I've attached a snapshot of the screen.

And, in case it's useful, some notable outputs:

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5200]
```

```
$ cat /etc/X11/xorg.conf 

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

```
$ xrandr
Screen 0: minimum 320 x 200, current 2400 x 1200, maximum 8192 x 8192
VGA-0 connected 800x600+1600+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050      60.0 +
   1600x1200      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0*    60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS connected 1600x1200+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   1600x1200      60.0*+   60.0     50.0  
   1400x1050      60.0  
   1280x1024      59.9     60.0  
   1440x900       59.9  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        60.0     59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)
```


Sorry for adding another thread to the post-release woes pile, but I couldn't find anything that worked on google, and I figured I'd see if anyone here has any insights...

---

### Post by danielinteractive on 2010-04-30
I am in the same situation. After upgrade from 9.10 to 10.04 (RC, but the release did not have any updates today) my VGA screen (Samsung SyncMaster 2043WM) goes mad. Also, the screen is perhaps not correctly detected, in the screen settings it is just "Samsung Electric Company 20''", but not the model?

More information:

The graphics card:
```

$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

```xorg.conf is not very informative (at least for me):
```

$ cat /etc/X11/xorg.conf 

Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    3080 1050
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

```And the screen resolutions (note that the native resolution of VGA-0 is 1680x1050):
```

$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9 +
   1280x1024      75.0     60.0* 
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS connected 1280x1024+0+0 (normal left inverted right x axis y axis) 287mm x 215mm
   1400x1050      60.0 +   50.0  
   1280x1024      59.9*    60.0  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        60.0     59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)

```Thank you very much for your help.

Daniel

---

### Post by blacflame on 2010-04-30
Summary - Same as above. The extended monitor is wavy as if it was completely out of  sync. If I only use one monitor (regardless of which one) its fine. But  if I extend then it dies out. 

Details/scenario

Hardware: IBM/Lenovo T60p, ATI Mobility (M56GL) FireGL v5250
Dell 2007wfp connected via VGA(analog)

Software: Ubuntu 10.04 LTS -  2.6.32-21-generic #32-Ubuntu i686
Driver: radeon KMS, (ATI quit supporting this as of ati-8.583 which  doesn't want run on this kernel)

All packages are standard from ubuntu repos 
KMS is enabled is operating as should from what i can tell 
$dmesg | grep drm
```
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera)  (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16  08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[   12.768299] [drm] Initialized drm 1.1.0 20060810
[   12.887617] [drm] radeon defaulting to kernel modesetting.
[   12.887620] [drm] radeon kernel modesetting enabled.
[   12.889181] [drm] radeon: Initializing kernel modesetting.
[   12.890813] [drm] register mmio base: 0xEE100000
[   12.890815] [drm] register mmio size: 65536
[   12.891131] [drm] GPU reset succeed (RBBM_STATUS=0x10000140)
[   12.891161] [drm] Generation 2 PCI interface, using max accessible  memory
[   12.891163] [drm] radeon: VRAM 256M
[   12.891165] [drm] radeon: VRAM from 0x00000000 to 0x0FFFFFFF
[   12.891167] [drm] radeon: GTT 512M
[   12.891168] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   12.891293] [drm] radeon: using MSI.
[   12.891339] [drm] radeon: irq initialized.
[   12.892760] [drm] Detected VRAM RAM=256M, BAR=256M
[   12.892762] [drm] RAM width 128bits DDR
[   12.895935] [drm] radeon: 256M of VRAM memory ready
[   12.895937] [drm] radeon: 512M of GTT memory ready.
[   12.895951] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   12.897475] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[   12.897531] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   12.897557] [drm] radeon: cp idle (0x10000C03)
[   12.897601] [drm] Loading R500 Microcode
[   12.901481] [drm] radeon: ring at 0x0000000020000000
[   12.901533] [drm] ring test succeeded in 4 usecs
[   12.901698] [drm] radeon: ib pool ready.
[   12.901783] [drm] ib test succeeded in 0 usecs
[   12.901941] [drm] Radeon Display Connectors
[   12.901943] [drm] Connector 0:
[   12.901945] [drm]   VGA
[   12.901947] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48  0x7e4c 0x7e4c
[   12.901949] [drm]   Encoders:
[   12.901950] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   12.901952] [drm] Connector 1:
[   12.901953] [drm]   LVDS
[   12.901955] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68  0x7e6c 0x7e6c
[   12.901957] [drm]   Encoders:
[   12.901958] [drm]     LCD1: INTERNAL_LVTM1
[   12.901960] [drm] Connector 2:
[   12.901961] [drm]   DVI-I
[   12.901962] [drm]   HPD1
[   12.901964] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58  0x7e5c 0x7e5c
[   12.901966] [drm]   Encoders:
[   12.901967] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[   13.264608] [drm] fb mappable at 0xD00C0000
[   13.264611] [drm] vram apper at 0xD0000000
[   13.264613] [drm] size 7257600
[   13.264614] [drm] fb depth is 24
[   13.264616] [drm]    pitch is 6912
[   13.265044] fb0: radeondrmfb frame buffer device
[   13.265052] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0  on minor 0

```Now I would of enabled a xorg.conf fully detailed with the  options however this part is throwing me off... xrandr says the monitor  is operating in the correct mode currently, and i'm getting a display  just out of sync (all wavy like an old tv set). and i'm not sure the  xorg.conf will make a difference with the radeon being KMS??

$xrandr -q --verbose

          ```
Screen 0: minimum 320 x 200, current 1680 x 2100,  maximum 8192 x 8192
VGA-0 connected 1680x1050+0+0 (0x54) normal (normal left inverted right x  axis y axis) 434mm x 270mm
    Identifier: 0x51
    Timestamp:  5848127
    Subpixel:   no subpixels
    Clones:     DVI-0
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff0010ac18a04c503433
        121001030e2b1b78eeee91a3544c9926
        0f5054a54b008180714f010101010101
        01010101010121399030621a274068b0
        3600b20e1100001c000000ff00484637
        33303635343334504c0a000000fc0044
        454c4c20323030375746500a000000fd
        00384c1e530f000a20202020202000eb
    load detection: 1 (0x00000001)    range:  (0,1)
  1680x1050 (0x54)  146.2MHz -HSync +VSync *current +preferred
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock    65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock    60.0Hz
  1280x1024 (0x55)  135.0MHz +HSync +VSync
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock    80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock    75.0Hz
  1280x1024 (0x56)  108.0MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock    64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock    60.0Hz
  1152x864 (0x57)  108.0MHz +HSync +VSync
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock    67.5KHz
        v: height  864 start  865 end  868 total  900           clock    75.0Hz
  1024x768 (0x58)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock    60.1KHz
        v: height  768 start  769 end  772 total  800           clock    75.1Hz
  1024x768 (0x59)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock    48.4KHz
        v: height  768 start  771 end  777 total  806           clock    60.0Hz
  800x600 (0x5a)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock    46.9KHz
        v: height  600 start  601 end  604 total  625           clock    75.0Hz
  800x600 (0x5b)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock    37.9KHz
        v: height  600 start  601 end  605 total  628           clock    60.3Hz
  640x480 (0x5c)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock    37.5KHz
        v: height  480 start  481 end  484 total  500           clock    75.0Hz
  640x480 (0x5d)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock    31.5KHz
        v: height  480 start  490 end  492 total  525           clock    60.0Hz
  720x400 (0x5e)   28.3MHz -HSync +VSync
        h: width   720 start  738 end  846 total  900 skew    0 clock    31.5KHz
        v: height  400 start  412 end  414 total  449           clock    70.1Hz
LVDS connected 1680x1050+0+1050 (0x60) normal (normal left inverted  right x axis y axis) 331mm x 207mm
    Identifier: 0x52
    Timestamp:  5848127
    Subpixel:   horizontal rgb
    Clones:    
    CRTC:       1
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID:
        00ffffffffffff00244d872800000000
        000f0103802115780abca59858558b28
        24505400000001010101010101010101
        0101010101011c2f90d0601a0f402030
        13004bcf10000019452790d0601a0f40
        203013004bcf100000190000000f00b3
        0a32b30a28140100320c0000000000fe
        004c503135345730322d544c303600bf
    scaling mode:    Full
        supported: None         Full         Center       Full aspect 
  1680x1050 (0x5f)  120.6MHz -HSync -VSync +preferred
        h: width  1680 start 1712 end 1760 total 1888 skew    0 clock    63.9KHz
        v: height 1050 start 1051 end 1054 total 1065           clock    60.0Hz
  1680x1050 (0x60)  100.5MHz -HSync -VSync *current
        h: width  1680 start 1712 end 1760 total 1888 skew    0 clock    53.2KHz
        v: height 1050 start 1051 end 1054 total 1065           clock    50.0Hz
  1400x1050 (0x61)  121.8MHz -HSync +VSync
        h: width  1400 start 1488 end 1632 total 1864 skew    0 clock    65.3KHz
        v: height 1050 start 1053 end 1057 total 1089           clock    60.0Hz
  1280x1024 (0x62)  109.0MHz -HSync +VSync
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock    63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock    59.9Hz
  1440x900 (0x63)  106.5MHz -HSync +VSync
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock    55.9KHz
        v: height  900 start  903 end  909 total  934           clock    59.9Hz
  1280x960 (0x64)  101.2MHz -HSync +VSync
        h: width  1280 start 1360 end 1488 total 1696 skew    0 clock    59.7KHz
        v: height  960 start  963 end  967 total  996           clock    59.9Hz
  1280x854 (0x65)   89.2MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock    53.1KHz
        v: height  854 start  857 end  867 total  887           clock    59.9Hz
  1280x800 (0x66)   83.5MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock    49.7KHz
        v: height  800 start  803 end  809 total  831           clock    59.8Hz
  1280x720 (0x67)   74.5MHz -HSync +VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock    44.8KHz
        v: height  720 start  723 end  728 total  748           clock    59.9Hz
  1152x768 (0x68)   71.8MHz -HSync +VSync
        h: width  1152 start 1216 end 1328 total 1504 skew    0 clock    47.7KHz
        v: height  768 start  771 end  781 total  798           clock    59.8Hz
  1024x768 (0x69)   63.5MHz -HSync +VSync
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock    47.8KHz
        v: height  768 start  771 end  775 total  798           clock    59.9Hz
  800x600 (0x6a)   38.2MHz -HSync +VSync
        h: width   800 start  832 end  912 total 1024 skew    0 clock    37.4KHz
        v: height  600 start  603 end  607 total  624           clock    59.9Hz
  848x480 (0x6b)   31.5MHz -HSync +VSync
        h: width   848 start  872 end  952 total 1056 skew    0 clock    29.8KHz
        v: height  480 start  483 end  493 total  500           clock    59.7Hz
  720x480 (0x6c)   26.8MHz -HSync +VSync
        h: width   720 start  744 end  808 total  896 skew    0 clock    29.9KHz
        v: height  480 start  483 end  493 total  500           clock    59.7Hz
  640x480 (0x6d)   23.8MHz -HSync +VSync
        h: width   640 start  664 end  720 total  800 skew    0 clock    29.7KHz
        v: height  480 start  483 end  487 total  500           clock    59.4Hz
DVI-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x53
    Timestamp:  5848127
    Subpixel:   horizontal rgb
    Clones:     VGA-0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    load detection: 1 (0x00000001)    range:  (0,1)
    coherent: 1 (0x00000001)    range:  (0,1)

```for 1680x1050 over analog the pix clock is 146.25 and hsync 65.3  vsync 60 based off Dell's [specs]("http://support.dell.com/support/edocs/monitors/2007WFP/en/about.htm#Specifications") - 

Now I decided to enable a custom xorg.conf and then just enable the  extra screen via xrandr after log in which is what i use to do with  Fedora 11 (however with KMS the monitor is already recognized and  extended so i dont' know the xorg.conf makes any difference?) 
Here's the xorg.conf regardless
```
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
    Load  "extmod"
    Load  "dri"
    Load  "dri2"
    Load  "glx"
    Load  "dbe"
    Load  "record"
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
    #DisplaySize      330   210    # mm
    Identifier   "Monitor0"
    VendorName   "IBM"
    ModelName    "2887"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>:  "True"/"False",
        ### <string>: "String", <freq>: "<f>  Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "Dac8Bit"                # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "CPPIOMode"              # [<bool>]
        #Option     "CPusecTimeout"          # <i>
        #Option     "AGPMode"                # <i>
        #Option     "AGPFastWrite"           # [<bool>]
        #Option     "AGPSize"                # <i>
        #Option     "GARTSize"               # <i>
        #Option     "RingSize"               # <i>
        #Option     "BufferSize"             # <i>
        #Option     "EnableDepthMoves"       # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "NoBackBuffer"           # [<bool>]
        #Option     "DMAForXv"               # [<bool>]
        #Option     "FBTexPercent"           # <i>
        #Option     "DepthBits"              # <i>
        #Option     "PCIAPERSize"            # <i>
        #Option     "AccelDFS"               # [<bool>]
        #Option     "IgnoreEDID"             # [<bool>]
        #Option     "CustomEDID"             # [<str>]
        #Option     "DisplayPriority"        # [<str>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForceMinDotClock"       # <freq>
        #Option     "ColorTiling"            # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "RageTheatreCrystal"     # <i>
        #Option     "RageTheatreTunerPort"     # <i>
        #Option     "RageTheatreCompositePort"     # <i>
        #Option     "RageTheatreSVideoPort"     # <i>
        #Option     "TunerType"              # <i>
        #Option     "RageTheatreMicrocPath"     # <str>
        #Option     "RageTheatreMicrocType"     # <str>
        #Option     "ScalerWidth"            # <i>
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "ClockGating"            # [<bool>]
        #Option     "VGAAccess"              # [<bool>]
        #Option     "ReverseDDC"             # [<bool>]
        #Option     "LVDSProbePLL"           # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "DRI"                    # [<bool>]
        #Option     "ConnectorTable"         # <str>
        #Option     "DefaultConnectorTable"     # [<bool>]
        #Option     "DefaultTMDSPLL"         # [<bool>]
        #Option     "TVDACLoadDetect"        # [<bool>]
        #Option     "ForceTVOut"             # [<bool>]
        #Option     "TVStandard"             # <str>
        #Option     "IgnoreLidStatus"        # [<bool>]
        #Option     "DefaultTVDACAdj"        # [<bool>]
        #Option     "Int10"                  # [<bool>]
        #Option     "EXAVSync"               # [<bool>]
        #Option     "ATOMTVOut"              # [<bool>]
        #Option     "R4xxATOM"               # [<bool>]
        #Option     "ForceLowPowerMode"      # [<bool>]
        #Option     "DynamicPM"              # [<bool>]
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "M56GL [Mobility FireGL V5250]"
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

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```I've search around and (the same i would think) most issues are  relevant to xorg loading the wrong modeline. Also nothing that says  M56GL isn't supported by radeon driver or specific issues. The best part  is compiz loads up fine and runs with no issues. 

glxgears (on the problem screen with compiz enables and lots of ani's)
```
6166 frames in 5.0 seconds
6387 frames in 5.0 seconds
6201 frames in 5.0 seconds
6184 frames in 5.0 seconds
6305 frames in 5.0 seconds
6252 frames in 5.0 seconds
6450 frames in 5.0 seconds
6265 frames in 5.0 seconds
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 154015 requests (154012 known processed) with 0 events  remaining.

```glxinfo | grep vendor
```
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: DRI R300 Project

```glxinfo | grep direct
```

direct rendering: Yes
```

---

### Post by blacflame on 2010-04-30
Gangeli/Daniel, 

I notice both of you are using non-native/preferred resolutions on the external monitors. Do you have the same issue if you use a native resolution, or is the current resolution just the one xorg picked by default?

Might try changing modes via xrandr -


$xrandr --output VGA-0 --mode 1680x1050 


Let me know if this helps?

---

### Post by gangeli on 2010-04-30
Oh, sorry about that. The problem persists at native resolution (1680x1050, 60hz); the attached picture was taken when the monitor was at 1680x1050. The monitor actually doesn't even render at all at the lower resolutions.

---

### Post by mpurses on 2010-05-02
I have the same problem on my  Acer H233H monitor which is connect to my Dell E1505 Laptop (ATI graphics). The external monitor gives me wavy lines no matter what resolution I set it to. But my laptop is just fine.

---

### Post by danielinteractive on 2010-05-03
blacflame,

for me also the problem persists if I switch to the native resolution...

Laptop monitor is fine, except once compiz (I think) broke down and blocked the system by using the CPU (process "backend").

---

### Post by errorsson on 2010-05-03
The relevant bug might be [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/541501](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/541501)
and for me it worked to create file /etc/modprobe.d/radeon.conf with contents "options radeon new_pll=0 modeset=0" and reboot.

Apparently also fixed upstream: [http://bugs.freedesktop.org/show_bug.cgi?id=27278](http://bugs.freedesktop.org/show_bug.cgi?id=27278)

---

### Post by danielinteractive on 2010-05-03
errorsson,

thank you very much!! This fixes the issue for me :D
Just great to have my large screen back!

Thanks again,
Daniel

---

### Post by gangeli on 2010-05-03
The fix worked for me too. Thanks errorsonn!

---

### Post by craig_ka on 2010-05-04
Up til my upgrade to 10.04 I had my tv-out and vga working on my laptop with a little editing of xorg.conf.  Now I have the same problem as above when kms is enabled, but my tv-out works without any problems.  But when I disable kms the flicker on the vga goes away but my tv-out goes to black and white.  I was wondering if anyone else has seen this problem and if a later kernel will fix the kms flickering issue.  As of now I have to reboot and specify nomodeset in grub to disable kms when using my vga and do a normal reboot to go back to using my tv-out.

Sorry if I should start a new thread since this one is solved, but my problem stacks right on top of this one.

---

### Post by colmeweb on 2010-12-13
Hello,

 Applying these fixes are a little above my head. Could somebody walk me through this in noob speak please.

Thanks

---

