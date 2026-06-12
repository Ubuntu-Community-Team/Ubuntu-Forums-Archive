---
title: "lucid lynx - radeon 9600 + gallium struggle (flash)"
date: 2010-08-15
forum: Multimedia Software
---

### Post by dirty_harry on 2010-08-15
Hi everyone,

I decided that I need help!

2 weeks ago I started building a system out of some stuff I found at home and a few ebay orders:

AMD AthlonXP 1.8
MSI KT266 v1
ATI 9600se
seagate 120GB 
[...Webcam,SCSI-Scanner,DVD,etc...]


Well, as for the* ATI9600, which comes with an RV350*, I wasn't aware of the changes since catalyst 9.4 !
Catalyst 9.3 ([http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx)) was the last binary driver for rv350 and is not working with Xorg in Lucid Lynx.

To begin with the flash performance of the system was literally bad:
```

–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
performancetests.GraphicsTests (5 iterations) 
Testing different approaches for drawing.                                
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
method...................................................ttl ms...avg ms 
tare [2]                                                      1     0.20 
drawPath                                                    485    97.00 
drawPathShort                                               389    77.80 
fullPath                                                    374    74.80 
reference                                                   345    69.00 
shortReference                                              292    58.40 
withGraphics                                               2744   548.80 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
performancetests.Functions (5 iterations) 
Testing impact of function COs.                                          
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
method...................................................ttl ms...avg ms 
tare [2]                                                      1     0.20 
anonymous                                                  2108   421.60 
anonymousRef                                                 53    10.60 
method                                                       11     2.20 
reference                                                    33     6.60 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
performancetests.Scope (5 iterations) 
Testing impact of scope.                                                 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
method...................................................ttl ms...avg ms 
tare [3]                                                    127    25.40 
constants                                                     1     0.20 
instance                                                      1     0.20 
instanceExplicit                                              0     0.00 
literals                                                      8     1.60 
local                                                         9     1.80 
staticExplicit                                              617   123.40 
staticVars                                                    2     0.40 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
performancetests.numeric.ArrayIterators (5 iterations) 
Tests performance of different numeric types as loop iterators.          
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
method...................................................ttl ms...avg ms 
intTest                                                    1142   228.40 
numberTest                                                 1587   317.40 
uintTest                                                   1070   214.00 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
performancetests.numeric.VectorIterators (5 iterations) 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
method...................................................ttl ms...avg ms 
intTest                                                     286    57.20 
numberTest                                                  809   161.80 
uintTest                                                    168    33.60 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
performancetests.Loops (5 iterations) 
Test different loop structures.                                          
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
method...................................................ttl ms...avg ms 
forIncrement                                                 28     5.60 
forDecrement                                                 26     5.20 
*                                                                          
whileIncrement                                               26     5.20 
whileDecrement                                              335    67.00 
*                                                                          
doWhileIncrement                                            281    56.20 
doWhileDecrement                                            280    56.00 
*                                                                          
forIn                                                       435    87.00 
forEachIn                                                   475    95.00 
forEachInUntyped                                            702   140.40 
forEachInPosttyped                                          571   114.20 
*                                                                          
arrForEach                                                  654   130.80 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
testFunction (5 iterations) 
this is a quick test of testFunction                                     
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
method...................................................ttl ms...avg ms 
[function]                                                   59    11.80 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
testRender (10 iterations) 
this is a quick test of testRender                                       
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
method...................................................ttl ms...avg ms 
tare [5]                                                     64     6.40 
[render]                                                     11     1.10 
–––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––– 
 
 
```This bench is from [*"gskinner.com gblog_ as3 performance testing harness"*]("http://www.gskinner.com/blog/archives/2009/04/as3_performance.html"), the only one I found for flash! For example my 2 year old asus notebook is three times faster with 9.04 and 50 open taps. For flash installation I used the FlashAid-plugin!
And watch streaming videos(youtube,etc) tells the same.


Somewhere I read that flash performance is link to graphic performance! So I searched for alternatives to catalyst and found out that people had made good use of the open-source radeon driver in combination with gallium(ppa edgers...).




I tried to reproduce this but failed tremendously :(. 
howto/tuts/etc I found:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1492357](http://ubuntuforums.org/showthread.php?t=1492357)
[http://www.phoronix.com/forums/archive/index.php/t-21708.html](http://www.phoronix.com/forums/archive/index.php/t-21708.html)



**glxinfo**:
```

                                 :~$ glxinfo | grep render  
 direct rendering: Yes  
 OpenGL renderer string: Gallium 0.4 on softpipe  
     GL_NV_blend_square, GL_NV_conditional_render, GL_NV_light_max_exponent,  
 

 :~$ glxinfo | grep vendor  
 server glx vendor string: SGI  
 client glx vendor string: Mesa Project and SGI  
 OpenGL vendor string: VMware, Inc.  
 

 :~$ glxinfo | grep version  
 server glx version string: 1.4  
 client glx version string: 1.4  
 GLX version: 1.4  
 OpenGL version string: 2.1 Mesa 7.9-devel  
 OpenGL shading language version string: 1.20  
 

  :~$ glxgears  
 Illegal instruction  
 

 :~$ glxgears -info  
 GL_RENDERER   = Gallium 0.4 on softpipe 
 GL_VERSION    = 2.1 Mesa 7.9-devel  
 GL_VENDOR     = VMware, Inc.  
 

   :~$ dmesg | grep vga  
 [    0.040770] vgaarb: loaded  
 [    0.043068] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none  
 [   16.462029] vga16fb: initializing  
 [   16.462046] vga16fb: mapped to 0xc00a0000  
 

  :~$ lspci | grep VGA  
 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]  
 
```glxgears isn't responding and I don't know how to switch off softpipe for Gallium!

Any hints are welcome! Even suggestions for a different way to go!

#######################

**What I tried so far:**
* fglrx - install, uninstall
* radeon - install, uninstall
* switch off KMS
* added ppa rep to install edgers ([https://edge.launchpad.net/~xorg-edgers/+archive/ppa]("https://edge.launchpad.net/%7Exorg-edgers/+archive/ppa"))
* modification of xorg.conf

**xorg.conf:**
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
    Load  "glx"
    Load  "extmod"
    Load  "record"
    Load  "dri2"
    Load  "dbe"
    Load  "dri"
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
    #DisplaySize      340   270    # mm
    Identifier   "Monitor0"
    VendorName   "MED"
    ModelName    "MD6155AN"
    HorizSync    30.0 - 82.0
    VertRefresh  50.0 - 75.0
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
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
        #Option     "Gallium"                # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV350 AQ [Radeon 9600]"
    BusID       "PCI:1:0:0"
    Option "AccelMethod" "XAA"
    # XAA/EXA
    Option "AccelDFS"    "0"
     # 1/0 On for PCIE, off for AGP
    # Manpage: Use  or  don't  use accelerated EXA DownloadFromScreenhook
    # when possible.
    Option "AGPMode" "4"
    # 1-8 Does not affect PCIE models.
    Option "AGPFastWrite" "1"
    # 1/0 Does not affect PCIE models. Not recommended.
    Option "GARTSize" "128"
    # 0-64 Megabytes of gart (system) memory used.
    # Wrongly defaults to 8MB sometimes, see your logfile.
    # Bigger seems better.
    Option "EnablePageFlip" "1"
    # 1/0 Increases 3D performance substantially
    # seemingly in XAA mode only
    Option "ColorTiling" "1"
    # 1/0 Increases 3D performance substantially
    # affected stability only positively on my system    
EndSection

Section "DRI"
     Group        "video"
     Mode         0666
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

Section "Extensions"
  Option      "Composite"     "Enable" # for 3D, alpha desktop effects
EndSection

```**Xorg.0.log:**
```

[    16.918] 
X.Org X Server 1.8.2
Release Date: 2010-07-01
[    16.919] X Protocol Version 11, Revision 0
[    16.919] Build Operating System: Linux 2.6.24-28-xen i686 Ubuntu
[    16.919] Current Operating System: Linux superkasten 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686
[    16.919] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=f885f1e6-d1c0-4762-b1f2-6cb9ba56119b ro quiet splash
[    16.919] Build Date: 08 July 2010  01:50:14AM
[    16.919] xorg-server 2:1.8.2+git20100705+server-1.8-branch.665aa7ce-0ubuntu0sarvatt2~lucid (For technical support please see http://www.ubuntu.com/support) 
[    16.919] Current version of pixman: 0.19.1
[    16.919]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    16.919] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.919] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 15 12:02:51 2010
[    16.920] (==) Using config file: "/etc/X11/xorg.conf"
[    16.920] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.937] (==) ServerLayout "X.org Configured"
[    16.937] (**) |-->Screen "Screen0" (0)
[    16.937] (**) |   |-->Monitor "Monitor0"
[    16.938] (**) |   |-->Device "Card0"
[    16.938] (**) |-->Input Device "Mouse0"
[    16.938] (**) |-->Input Device "Keyboard0"
[    16.938] (==) Automatically adding devices
[    16.938] (==) Automatically enabling devices
[    16.938] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.938]     Entry deleted from font path.
[    16.938] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.939]     Entry deleted from font path.
[    16.939] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    16.939] (**) ModulePath set to "/usr/lib/xorg/modules"
[    16.939] (**) Extension "Composite" is enabled
[    16.940] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    16.940] (WW) Disabling Mouse0
[    16.940] (WW) Disabling Keyboard0
[    16.940] (II) Loader magic: 0x81f4ba0
[    16.940] (II) Module ABI versions:
[    16.940]     X.Org ANSI C Emulation: 0.4
[    16.940]     X.Org Video Driver: 7.0
[    16.940]     X.Org XInput driver : 9.0
[    16.940]     X.Org Server Extension : 3.0
[    17.040] (--) PCI:*(0:1:0:0) 1002:4151:1043:c004 ATI Technologies Inc RV350 AQ [Radeon 9600] rev 0, Mem @ 0xc0000000/268435456, 0xdfef0000/65536, I/O @ 0x00009800/256, BIOS @ 0x????????/131072
[    17.040] (--) PCI: (0:1:0:1) 1002:4171:1043:c005 ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary) rev 0, Mem @ 0xb0000000/268435456, 0xdfee0000/65536
[    17.041] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.041] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    17.041] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    17.041] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    17.041] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    17.041] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    17.041] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[    17.041] (II) LoadModule: "glx"
[    17.043] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.043] (II) Module glx: vendor="X.Org Foundation"
[    17.044]     compiled for 1.8.2, module version = 1.0.0
[    17.044]     ABI class: X.Org Server Extension, version 3.0
[    17.044] (==) AIGLX enabled
[    17.044] (II) Loading extension GLX
[    17.044] (II) LoadModule: "extmod"
[    17.044] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.045] (II) Module extmod: vendor="X.Org Foundation"
[    17.045]     compiled for 1.8.2, module version = 1.0.0
[    17.045]     Module class: X.Org Server Extension
[    17.045]     ABI class: X.Org Server Extension, version 3.0
[    17.045] (II) Loading extension MIT-SCREEN-SAVER
[    17.045] (II) Loading extension XFree86-VidModeExtension
[    17.045] (II) Loading extension XFree86-DGA
[    17.045] (II) Loading extension DPMS
[    17.045] (II) Loading extension XVideo
[    17.045] (II) Loading extension XVideo-MotionCompensation
[    17.045] (II) Loading extension X-Resource
[    17.045] (II) LoadModule: "record"
[    17.045] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.046] (II) Module record: vendor="X.Org Foundation"
[    17.046]     compiled for 1.8.2, module version = 1.13.0
[    17.046]     Module class: X.Org Server Extension
[    17.046]     ABI class: X.Org Server Extension, version 3.0
[    17.046] (II) Loading extension RECORD
[    17.046] (II) LoadModule: "dri2"
[    17.046] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.047] (II) Module dri2: vendor="X.Org Foundation"
[    17.047]     compiled for 1.8.2, module version = 1.2.0
[    17.047]     ABI class: X.Org Server Extension, version 3.0
[    17.047] (II) Loading extension DRI2
[    17.047] (II) LoadModule: "dbe"
[    17.047] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.048] (II) Module dbe: vendor="X.Org Foundation"
[    17.048]     compiled for 1.8.2, module version = 1.0.0
[    17.048]     Module class: X.Org Server Extension
[    17.048]     ABI class: X.Org Server Extension, version 3.0
[    17.048] (II) Loading extension DOUBLE-BUFFER
[    17.048] (II) LoadModule: "dri"
[    17.048] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.048] (II) Module dri: vendor="X.Org Foundation"
[    17.049]     compiled for 1.8.2, module version = 1.0.0
[    17.049]     ABI class: X.Org Server Extension, version 3.0
[    17.049] (II) Loading extension XFree86-DRI
[    17.049] (II) LoadModule: "radeon"
[    17.049] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    17.050] (II) Module radeon: vendor="X.Org Foundation"
[    17.050]     compiled for 1.8.2, module version = 6.13.99
[    17.050]     Module class: X.Org Video Driver
[    17.050]     ABI class: X.Org Video Driver, version 7.0
[    17.050] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR
[    17.063] (++) using VT number 7

[    17.069] (II) Primary Device is: PCI 01@00:00:0
[    17.069] (II) [KMS] drm report modesetting isn't supported.
[    17.070] (II) RADEON(0): TOTO SAYS 00000000dfef0000
[    17.070] (II) RADEON(0): MMIO registers at 0x00000000dfef0000: size 64KB
[    17.070] (II) RADEON(0): PCI bus 1 card 0 func 0
[    17.070] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    17.070] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    17.070] (==) RADEON(0): Default visual is TrueColor
[    17.070] (**) RADEON(0): Option "AGPMode" "4"
[    17.070] (**) RADEON(0): Option "AGPFastWrite" "1"
[    17.070] (**) RADEON(0): Option "GARTSize" "128"
[    17.070] (**) RADEON(0): Option "EnablePageFlip" "1"
[    17.070] (**) RADEON(0): Option "AccelDFS" "0"
[    17.070] (**) RADEON(0): Option "ColorTiling" "1"
[    17.070] (**) RADEON(0): Option "AccelMethod" "XAA"
[    17.071] (II) Loading sub module "vgahw"
[    17.071] (II) LoadModule: "vgahw"
[    17.071] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    17.084] (II) Module vgahw: vendor="X.Org Foundation"
[    17.085]     compiled for 1.8.2, module version = 0.1.0
[    17.085]     ABI class: X.Org Video Driver, version 7.0
[    17.085] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    17.085] (==) RADEON(0): RGB weight 888
[    17.085] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    17.085] (--) RADEON(0): Chipset: "ATI Radeon 9600SE AQ (AGP)" (ChipID = 0x4151)
[    17.085] (--) RADEON(0): Linear framebuffer at 0x00000000c0000000
[    17.085] (II) RADEON(0): AGP card detected
[    17.085] (II) Loading sub module "int10"
[    17.085] (II) LoadModule: "int10"
[    17.085] (II) Loading /usr/lib/xorg/modules/libint10.so
[    17.093] (II) Module int10: vendor="X.Org Foundation"
[    17.093]     compiled for 1.8.2, module version = 1.0.0
[    17.093]     ABI class: X.Org Video Driver, version 7.0
[    17.093] (II) RADEON(0): initializing int10
[    17.099] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    17.102] (II) RADEON(0): Legacy BIOS detected
[    17.102] drmOpenDevice: node name is /dev/dri/card0
[    17.358] [drm] failed to load kernel module "radeon"
[    17.358] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    17.358] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    17.358] (II) RADEON(0): Detected total video RAM=131072K, accessible=262144K (PCI BAR=262144K)
[    17.358] (--) RADEON(0): Mapped VideoRAM: 131072 kByte (64 bit DDR SDRAM)
[    17.358] (II) RADEON(0): Color tiling enabled by default
[    17.358] (II) Loading sub module "ddc"
[    17.358] (II) LoadModule: "ddc"
[    17.358] (II) Module "ddc" already built-in
[    17.358] (II) Loading sub module "i2c"
[    17.358] (II) LoadModule: "i2c"
[    17.358] (II) Module "i2c" already built-in
[    17.358] (II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 40, max_in_pll: 3000, xclk: 19900, sclk: 325.000000, mclk: 199.000000
[    17.358] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=19900
[    17.358] (II) RADEON(0): DFP table revision: 3
[    17.358] (II) RADEON(0): Output VGA-0 using monitor section Monitor0
[    17.358] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    17.358] (II) RADEON(0): Output DVI-0 has no monitor section
[    17.359] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    17.359] (II) RADEON(0): Output S-video has no monitor section
[    17.359] (II) RADEON(0): Default TV standard: PAL
[    17.359] (II) RADEON(0): TV standards supported by chip: NTSC PAL 
[    17.359] (II) RADEON(0): Port0:
[    17.359]   XRANDR name: VGA-0
[    17.359]   Connector: VGA
[    17.359]   CRT1: INTERNAL_DAC1
[    17.359]   DDC reg: 0x60
[    17.359] (II) RADEON(0): Port1:
[    17.359]   XRANDR name: DVI-0
[    17.359]   Connector: DVI-I
[    17.359]   CRT2: INTERNAL_DAC2
[    17.359]   DFP1: INTERNAL_TMDS1
[    17.359]   DDC reg: 0x64
[    17.359] (II) RADEON(0): Port2:
[    17.359]   XRANDR name: S-video
[    17.359]   Connector: S-video
[    17.359]   TV1: INTERNAL_DAC2
[    17.359]   DDC reg: 0x0
[    17.359] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    17.414] (II) RADEON(0): EDID for output VGA-0
[    17.414] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    17.414] (II) RADEON(0): Year: 2003  Week: 4
[    17.414] (II) RADEON(0): EDID Version: 1.3
[    17.414] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    17.414] (II) RADEON(0): Sync:  Separate
[    17.414] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    17.415] (II) RADEON(0): Gamma: 2.20
[    17.415] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    17.415] (II) RADEON(0): First detailed timing is preferred mode
[    17.415] (II) RADEON(0): GTF timings supported
[    17.415] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    17.415] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    17.415] (II) RADEON(0): Supported established timings:
[    17.415] (II) RADEON(0): 720x400@70Hz
[    17.415] (II) RADEON(0): 640x480@60Hz
[    17.415] (II) RADEON(0): 640x480@67Hz
[    17.415] (II) RADEON(0): 640x480@72Hz
[    17.415] (II) RADEON(0): 640x480@75Hz
[    17.415] (II) RADEON(0): 800x600@56Hz
[    17.415] (II) RADEON(0): 800x600@60Hz
[    17.415] (II) RADEON(0): 800x600@72Hz
[    17.415] (II) RADEON(0): 800x600@75Hz
[    17.415] (II) RADEON(0): 832x624@75Hz
[    17.415] (II) RADEON(0): 1024x768@60Hz
[    17.415] (II) RADEON(0): 1024x768@70Hz
[    17.415] (II) RADEON(0): 1024x768@75Hz
[    17.415] (II) RADEON(0): 1280x1024@75Hz
[    17.415] (II) RADEON(0): Manufacturer's mask: 0
[    17.415] (II) RADEON(0): Supported standard timings:
[    17.415] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    17.415] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    17.415] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    17.415] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    17.415] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    17.415] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    17.415] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    17.415] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    17.415] (II) RADEON(0): Supported detailed timing:
[    17.415] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    17.416] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    17.416] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    17.416] (II) RADEON(0): Serial No: 27269
[    17.416] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    17.416] (II) RADEON(0): Monitor name: MD6155AN
[    17.416] (II) RADEON(0): EDID (in hex):
[    17.416] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    17.416] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    17.416] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    17.416] (II) RADEON(0):     4540454a454f302a009851002a403070
[    17.416] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    17.416] (II) RADEON(0):     36390000000000000000000000fd0032
[    17.416] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    17.416] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    17.416] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    17.416] (II) RADEON(0): Using hsync ranges from config file
[    17.416] (II) RADEON(0): Using vrefresh ranges from config file
[    17.416] (II) RADEON(0): Printing DDC gathered Modelines:
[    17.416] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.416] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.416] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    17.416] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.416] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    17.416] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    17.416] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.417] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    17.417] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.417] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.417] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    17.417] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.417] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    17.417] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.417] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    17.417] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    17.417] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    17.417] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    17.417] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    17.417] (II) RADEON(0): Year: 2003  Week: 4
[    17.417] (II) RADEON(0): EDID Version: 1.3
[    17.417] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    17.417] (II) RADEON(0): Sync:  Separate
[    17.417] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    17.417] (II) RADEON(0): Gamma: 2.20
[    17.417] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    17.417] (II) RADEON(0): First detailed timing is preferred mode
[    17.417] (II) RADEON(0): GTF timings supported
[    17.417] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    17.417] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    17.417] (II) RADEON(0): Supported established timings:
[    17.417] (II) RADEON(0): 720x400@70Hz
[    17.417] (II) RADEON(0): 640x480@60Hz
[    17.417] (II) RADEON(0): 640x480@67Hz
[    17.417] (II) RADEON(0): 640x480@72Hz
[    17.418] (II) RADEON(0): 640x480@75Hz
[    17.418] (II) RADEON(0): 800x600@56Hz
[    17.418] (II) RADEON(0): 800x600@60Hz
[    17.418] (II) RADEON(0): 800x600@72Hz
[    17.418] (II) RADEON(0): 800x600@75Hz
[    17.418] (II) RADEON(0): 832x624@75Hz
[    17.418] (II) RADEON(0): 1024x768@60Hz
[    17.418] (II) RADEON(0): 1024x768@70Hz
[    17.418] (II) RADEON(0): 1024x768@75Hz
[    17.418] (II) RADEON(0): 1280x1024@75Hz
[    17.418] (II) RADEON(0): Manufacturer's mask: 0
[    17.418] (II) RADEON(0): Supported standard timings:
[    17.418] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    17.418] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    17.418] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    17.418] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    17.418] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    17.418] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    17.418] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    17.418] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    17.418] (II) RADEON(0): Supported detailed timing:
[    17.418] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    17.418] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    17.418] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    17.418] (II) RADEON(0): Serial No: 27269
[    17.418] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    17.418] (II) RADEON(0): Monitor name: MD6155AN
[    17.418] (II) RADEON(0): EDID (in hex):
[    17.418] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    17.418] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    17.418] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    17.418] (II) RADEON(0):     4540454a454f302a009851002a403070
[    17.418] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    17.419] (II) RADEON(0):     36390000000000000000000000fd0032
[    17.419] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    17.419] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    17.419] finished output detect: 0
[    17.419] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    17.423] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    17.423] Unhandled monitor type 0
[    17.423] finished output detect: 1
[    17.423] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    17.423] finished output detect: 2
[    17.423] finished all detect
[    17.478] (II) RADEON(0): EDID for output VGA-0
[    17.478] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    17.478] (II) RADEON(0): Year: 2003  Week: 4
[    17.478] (II) RADEON(0): EDID Version: 1.3
[    17.478] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    17.478] (II) RADEON(0): Sync:  Separate
[    17.478] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    17.478] (II) RADEON(0): Gamma: 2.20
[    17.478] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    17.478] (II) RADEON(0): First detailed timing is preferred mode
[    17.478] (II) RADEON(0): GTF timings supported
[    17.478] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    17.478] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    17.478] (II) RADEON(0): Supported established timings:
[    17.478] (II) RADEON(0): 720x400@70Hz
[    17.478] (II) RADEON(0): 640x480@60Hz
[    17.478] (II) RADEON(0): 640x480@67Hz
[    17.478] (II) RADEON(0): 640x480@72Hz
[    17.479] (II) RADEON(0): 640x480@75Hz
[    17.479] (II) RADEON(0): 800x600@56Hz
[    17.479] (II) RADEON(0): 800x600@60Hz
[    17.479] (II) RADEON(0): 800x600@72Hz
[    17.479] (II) RADEON(0): 800x600@75Hz
[    17.479] (II) RADEON(0): 832x624@75Hz
[    17.479] (II) RADEON(0): 1024x768@60Hz
[    17.479] (II) RADEON(0): 1024x768@70Hz
[    17.479] (II) RADEON(0): 1024x768@75Hz
[    17.479] (II) RADEON(0): 1280x1024@75Hz
[    17.479] (II) RADEON(0): Manufacturer's mask: 0
[    17.479] (II) RADEON(0): Supported standard timings:
[    17.479] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    17.479] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    17.479] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    17.479] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    17.479] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    17.479] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    17.479] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    17.479] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    17.479] (II) RADEON(0): Supported detailed timing:
[    17.479] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    17.479] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    17.479] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    17.479] (II) RADEON(0): Serial No: 27269
[    17.479] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    17.479] (II) RADEON(0): Monitor name: MD6155AN
[    17.479] (II) RADEON(0): EDID (in hex):
[    17.479] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    17.479] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    17.479] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    17.479] (II) RADEON(0):     4540454a454f302a009851002a403070
[    17.479] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    17.479] (II) RADEON(0):     36390000000000000000000000fd0032
[    17.480] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    17.480] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    17.480] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    17.480] (II) RADEON(0): Using hsync ranges from config file
[    17.480] (II) RADEON(0): Using vrefresh ranges from config file
[    17.480] (II) RADEON(0): Printing DDC gathered Modelines:
[    17.480] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.480] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.480] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    17.480] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.480] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    17.480] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    17.480] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.480] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    17.480] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.480] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.480] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    17.480] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.480] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    17.480] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.480] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    17.480] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    17.480] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    17.480] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    17.480] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    17.480] (II) RADEON(0): Year: 2003  Week: 4
[    17.480] (II) RADEON(0): EDID Version: 1.3
[    17.481] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    17.481] (II) RADEON(0): Sync:  Separate
[    17.481] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    17.481] (II) RADEON(0): Gamma: 2.20
[    17.481] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    17.481] (II) RADEON(0): First detailed timing is preferred mode
[    17.481] (II) RADEON(0): GTF timings supported
[    17.481] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    17.481] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    17.481] (II) RADEON(0): Supported established timings:
[    17.481] (II) RADEON(0): 720x400@70Hz
[    17.481] (II) RADEON(0): 640x480@60Hz
[    17.481] (II) RADEON(0): 640x480@67Hz
[    17.481] (II) RADEON(0): 640x480@72Hz
[    17.481] (II) RADEON(0): 640x480@75Hz
[    17.481] (II) RADEON(0): 800x600@56Hz
[    17.481] (II) RADEON(0): 800x600@60Hz
[    17.481] (II) RADEON(0): 800x600@72Hz
[    17.481] (II) RADEON(0): 800x600@75Hz
[    17.481] (II) RADEON(0): 832x624@75Hz
[    17.481] (II) RADEON(0): 1024x768@60Hz
[    17.481] (II) RADEON(0): 1024x768@70Hz
[    17.481] (II) RADEON(0): 1024x768@75Hz
[    17.481] (II) RADEON(0): 1280x1024@75Hz
[    17.481] (II) RADEON(0): Manufacturer's mask: 0
[    17.481] (II) RADEON(0): Supported standard timings:
[    17.481] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    17.481] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    17.481] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    17.481] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    17.481] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    17.481] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    17.481] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    17.481] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    17.482] (II) RADEON(0): Supported detailed timing:
[    17.482] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    17.482] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    17.482] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    17.482] (II) RADEON(0): Serial No: 27269
[    17.482] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    17.482] (II) RADEON(0): Monitor name: MD6155AN
[    17.482] (II) RADEON(0): EDID (in hex):
[    17.482] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    17.482] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    17.482] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    17.482] (II) RADEON(0):     4540454a454f302a009851002a403070
[    17.482] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    17.482] (II) RADEON(0):     36390000000000000000000000fd0032
[    17.482] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    17.482] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    17.482] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    17.483] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    17.483] (II) RADEON(0): Not using default mode "320x175" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    17.483] (II) RADEON(0): Not using default mode "320x200" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    17.483] (II) RADEON(0): Not using default mode "360x200" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    17.483] (II) RADEON(0): Not using default mode "320x240" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    17.483] (II) RADEON(0): Not using default mode "400x300" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "1024x768i" (interlace mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "512x384i" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    17.483] (II) RADEON(0): Not using default mode "512x384" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
[    17.483] (II) RADEON(0): Not using default mode "640x480" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
[    17.483] (II) RADEON(0): Not using default mode "640x512" (doublescan mode not supported)
[    17.483] (II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    17.483] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "800x600" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "896x672" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "928x696" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "416x312" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    17.484] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    17.484] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "576x432" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    17.484] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "680x384" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.484] (II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    17.484] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "700x525" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "720x450" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "800x512" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
[    17.485] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "840x525" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
[    17.485] (II) RADEON(0): Not using default mode "960x540" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "960x600" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "960x720" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    17.485] (II) RADEON(0): Not using default mode "1024x768" (doublescan mode not supported)
[    17.485] (II) RADEON(0): Printing probed modes for output VGA-0
[    17.485] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.485] (II) RADEON(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
[    17.485] (II) RADEON(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
[    17.485] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.485] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.486] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    17.486] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    17.486] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    17.486] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    17.486] (II) RADEON(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
[    17.486] (II) RADEON(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[    17.486] (II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    17.486] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.486] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    17.486] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.486] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    17.486] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    17.486] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.486] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    17.486] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.486] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    17.486] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.486] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    17.486] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.486] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    17.486] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.486] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    17.491] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    17.491] Unhandled monitor type 0
[    17.491] (II) RADEON(0): EDID for output DVI-0
[    17.491] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    17.491] (II) RADEON(0): EDID for output S-video
[    17.491] (II) RADEON(0): Output VGA-0 connected
[    17.491] (II) RADEON(0): Output DVI-0 disconnected
[    17.491] (II) RADEON(0): Output S-video disconnected
[    17.491] (II) RADEON(0): Using exact sizes for initial modes
[    17.491] (II) RADEON(0): Output VGA-0 using initial mode 1280x1024
[    17.491] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.491] (**) RADEON(0): Display dimensions: (340, 270) mm
[    17.491] (**) RADEON(0): DPI set to (119, 150)
[    17.491] (II) Loading sub module "fb"
[    17.491] (II) LoadModule: "fb"
[    17.492] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.493] (II) Module fb: vendor="X.Org Foundation"
[    17.493]     compiled for 1.8.2, module version = 1.0.0
[    17.493]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.493] (II) Loading sub module "ramdac"
[    17.493] (II) LoadModule: "ramdac"
[    17.493] (II) Module "ramdac" already built-in
[    17.493] (**) RADEON(0): Using XAA acceleration architecture
[    17.493] (II) Loading sub module "xaa"
[    17.493] (II) LoadModule: "xaa"
[    17.503] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    17.527] (II) Module xaa: vendor="X.Org Foundation"
[    17.527]     compiled for 1.8.2, module version = 1.2.1
[    17.527]     ABI class: X.Org Video Driver, version 7.0
[    17.527] (==) RADEON(0): Assuming overlay scaler buffer width is 1920
[    17.527] (II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
[    17.528] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    17.528] (--) Depth 24 pixmap format is 32 bpp
[    17.528] (II) RADEON(0): RADEONScreenInit c0000000 0 0
[    17.533] Entering TV Save
[    17.533] Save TV timing tables
[    17.533] saveTimingTables: reading timing tables
[    17.533] TV Save done
[    17.533] disable primary dac
[    17.533] (II) RADEON(0): Dynamic Power Management Disabled
[    17.533] (II) RADEON(0): RADEONInitMemoryMap() : 
[    17.533] (II) RADEON(0):   mem_size         : 0x08000000
[    17.533] (II) RADEON(0):   MC_FB_LOCATION   : 0xc7ffc000
[    17.533] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.533] (II) RADEON(0): Depth moves disabled by default
[    17.533] (II) RADEON(0): Memory manager initialized to (0,0) (1600,8191)
[    17.533] (II) RADEON(0): Reserved area from (0,1600) to (1600,1602)
[    17.533] (II) RADEON(0): Largest offscreen area available: 1600 x 6589
[    17.534] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    17.534] (II) RADEON(0):   MC_FB_LOCATION   : 0xc7ffc000 0x1fff0000
[    17.534] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.738] (==) RADEON(0): Backing store disabled
[    17.738] (WW) RADEON(0): Direct rendering disabled
[    17.738] (II) RADEON(0): Render acceleration disabled
[    17.738] (II) RADEON(0): num quad-pipes is 1
[    17.738] (II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
[    17.739]     Screen to screen bit blits
[    17.739]     Solid filled rectangles
[    17.739]     8x8 mono pattern filled rectangles
[    17.739]     Indirect CPU to Screen color expansion
[    17.739]     Solid Lines
[    17.739]     Scanline Image Writes
[    17.739]     Setting up tile and stipple cache:
[    17.739]         32 128x128 slots
[    17.739]         32 256x256 slots
[    17.739]         16 512x512 slots
[    17.739] (II) RADEON(0): Acceleration enabled
[    17.739] (**) RADEON(0): DPMS enabled
[    17.739] (==) RADEON(0): Silken mouse enabled
[    17.739] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x009c7200
[    17.739] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x009cbd00
[    17.740] (II) RADEON(0): Largest offscreen area available: 1600 x 6583
[    17.740] (II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
[    17.740] (II) Loading sub module "theatre_detect"
[    17.740] (II) LoadModule: "theatre_detect"
[    17.740] (II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
[    17.750] (II) Module theatre_detect: vendor="X.Org Foundation"
[    17.750]     compiled for 1.8.2, module version = 1.0.0
[    17.750]     ABI class: X.Org Video Driver, version 7.0
[    17.750] (II) RADEON(0): no multimedia table present, disabling Rage Theatre.
[    17.750] (II) RADEON(0): Set up overlay video
[    17.751] (II) RADEON(0): Set up textured video
[    17.804] disable primary dac
[    17.804] disable TV
[    17.804] disable primary dac
[    17.804] init memmap
[    17.804] init common
[    17.804] init crtc1
[    17.804] init pll1
[    17.804] freq: 108000000
[    17.805] best_freq: 108000000
[    17.805] best_feedback_div: 16
[    17.805] best_frac_feedback_div: 0
[    17.805] best_ref_div: 2
[    17.805] best_post_div: 2
[    17.805] restore memmap
[    17.805] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    17.805] (II) RADEON(0):   MC_FB_LOCATION   : 0xc7ffc000 0xc7ffc000
[    17.805] (II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
[    17.906] restore common
[    17.906] restore crtc1
[    17.906] restore pll1
[    17.958] finished PLL1
[    17.958] set RMX
[    17.958] set primary dac
[    17.958] enable primary dac
[    17.958] disable TV
[    17.959] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.959] (--) RandR disabled
[    17.959] (II) Initializing built-in extension Generic Event Extension
[    17.959] (II) Initializing built-in extension SHAPE
[    17.959] (II) Initializing built-in extension MIT-SHM
[    17.959] (II) Initializing built-in extension XInputExtension
[    17.959] (II) Initializing built-in extension XTEST
[    17.959] (II) Initializing built-in extension BIG-REQUESTS
[    17.959] (II) Initializing built-in extension SYNC
[    17.959] (II) Initializing built-in extension XKEYBOARD
[    17.959] (II) Initializing built-in extension XC-MISC
[    17.959] (II) Initializing built-in extension SECURITY
[    17.959] (II) Initializing built-in extension XINERAMA
[    17.959] (II) Initializing built-in extension XFIXES
[    17.959] (II) Initializing built-in extension RENDER
[    17.959] (II) Initializing built-in extension RANDR
[    17.959] (II) Initializing built-in extension COMPOSITE
[    17.959] (II) Initializing built-in extension DAMAGE
[    17.977] (II) AIGLX: Screen 0 is not DRI2 capable
[    17.977] (II) AIGLX: Screen 0 is not DRI capable
[    18.018] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    18.018] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    18.019] (II) RADEON(0): Setting screen physical size to 338 x 270
[    18.136] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.160] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event1)
[    18.160] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.160] (II) LoadModule: "evdev"
[    18.161] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.161] (II) Module evdev: vendor="X.Org Foundation"
[    18.161]     compiled for 1.8.2, module version = 2.4.99
[    18.161]     Module class: X.Org XInput Driver
[    18.161]     ABI class: X.Org XInput driver, version 9.0
[    18.161] (**) AT Translated Set 2 keyboard: always reports core events
[    18.161] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
[    18.162] (--) AT Translated Set 2 keyboard: Found keys
[    18.162] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.162] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.162] (**) Option "xkb_rules" "evdev"
[    18.162] (**) Option "xkb_model" "evdev"
[    18.162] (**) Option "xkb_layout" "de"
[    18.167] (II) XKB: reuse xkmfile /var/lib/xkb/server-1B5353734E7854C1F2B0553E65A16986C9AAC402.xkm
[    18.169] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event2)
[    18.169] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    18.169] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    18.169] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event2"
[    18.170] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    18.170] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    18.170] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    18.170] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    18.170] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    18.170] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    18.170] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.170] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    18.170] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    18.170] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    18.170] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    18.170] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    18.170] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    18.171] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
[    18.171] (II) No input driver/identifier specified (ignoring)
[    18.178] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event0)
[    18.179] (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
[    18.179] (**) Macintosh mouse button emulation: always reports core events
[    18.179] (**) Macintosh mouse button emulation: Device: "/dev/input/event0"
[    18.179] (--) Macintosh mouse button emulation: Found 3 mouse buttons
[    18.179] (--) Macintosh mouse button emulation: Found relative axes
[    18.179] (--) Macintosh mouse button emulation: Found x and y relative axes
[    18.179] (II) Macintosh mouse button emulation: Configuring as mouse
[    18.179] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    18.179] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.179] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    18.179] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    18.179] (**) Macintosh mouse button emulation: (accel) acceleration profile 0
[    18.179] (**) Macintosh mouse button emulation: (accel) acceleration factor: 2.000
[    18.179] (**) Macintosh mouse button emulation: (accel) acceleration threshold: 4
[    18.179] (II) Macintosh mouse button emulation: initialized for relative axes.
[    18.180] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
[    18.180] (II) No input driver/identifier specified (ignoring)
[    19.129] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    19.129] (II) RADEON(0): Using hsync ranges from config file
[    19.129] (II) RADEON(0): Using vrefresh ranges from config file
[    19.129] (II) RADEON(0): Printing DDC gathered Modelines:
[    19.129] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    19.129] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.129] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.129] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    19.129] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    19.129] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    19.129] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.129] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    19.130] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    19.130] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    19.130] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    19.130] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.130] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    19.130] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    19.130] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    19.130] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    19.130] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    19.130] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    19.130] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    19.130] (II) RADEON(0): Year: 2003  Week: 4
[    19.130] (II) RADEON(0): EDID Version: 1.3
[    19.130] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    19.130] (II) RADEON(0): Sync:  Separate
[    19.130] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    19.130] (II) RADEON(0): Gamma: 2.20
[    19.130] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    19.130] (II) RADEON(0): First detailed timing is preferred mode
[    19.130] (II) RADEON(0): GTF timings supported
[    19.130] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    19.130] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    19.130] (II) RADEON(0): Supported established timings:
[    19.130] (II) RADEON(0): 720x400@70Hz
[    19.130] (II) RADEON(0): 640x480@60Hz
[    19.130] (II) RADEON(0): 640x480@67Hz
[    19.130] (II) RADEON(0): 640x480@72Hz
[    19.130] (II) RADEON(0): 640x480@75Hz
[    19.131] (II) RADEON(0): 800x600@56Hz
[    19.131] (II) RADEON(0): 800x600@60Hz
[    19.131] (II) RADEON(0): 800x600@72Hz
[    19.131] (II) RADEON(0): 800x600@75Hz
[    19.131] (II) RADEON(0): 832x624@75Hz
[    19.131] (II) RADEON(0): 1024x768@60Hz
[    19.131] (II) RADEON(0): 1024x768@70Hz
[    19.131] (II) RADEON(0): 1024x768@75Hz
[    19.131] (II) RADEON(0): 1280x1024@75Hz
[    19.131] (II) RADEON(0): Manufacturer's mask: 0
[    19.131] (II) RADEON(0): Supported standard timings:
[    19.131] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    19.131] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    19.131] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    19.131] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    19.131] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    19.131] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    19.131] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    19.131] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    19.131] (II) RADEON(0): Supported detailed timing:
[    19.131] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    19.131] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    19.131] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    19.131] (II) RADEON(0): Serial No: 27269
[    19.131] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    19.131] (II) RADEON(0): Monitor name: MD6155AN
[    19.131] (II) RADEON(0): EDID (in hex):
[    19.131] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    19.131] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    19.131] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    19.131] (II) RADEON(0):     4540454a454f302a009851002a403070
[    19.131] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    19.131] (II) RADEON(0):     36390000000000000000000000fd0032
[    19.132] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    19.132] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    19.132] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    19.137] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    19.137] Unhandled monitor type 0
[    19.137] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    19.195] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    19.195] (II) RADEON(0): Using hsync ranges from config file
[    19.195] (II) RADEON(0): Using vrefresh ranges from config file
[    19.195] (II) RADEON(0): Printing DDC gathered Modelines:
[    19.195] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    19.196] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.196] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.196] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    19.196] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    19.196] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    19.196] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.196] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    19.196] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    19.196] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    19.196] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    19.196] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.196] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    19.196] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    19.196] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    19.196] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    19.196] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    19.196] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    19.196] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    19.196] (II) RADEON(0): Year: 2003  Week: 4
[    19.196] (II) RADEON(0): EDID Version: 1.3
[    19.196] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    19.196] (II) RADEON(0): Sync:  Separate
[    19.196] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    19.196] (II) RADEON(0): Gamma: 2.20
[    19.196] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    19.197] (II) RADEON(0): First detailed timing is preferred mode
[    19.197] (II) RADEON(0): GTF timings supported
[    19.197] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    19.197] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    19.197] (II) RADEON(0): Supported established timings:
[    19.197] (II) RADEON(0): 720x400@70Hz
[    19.197] (II) RADEON(0): 640x480@60Hz
[    19.197] (II) RADEON(0): 640x480@67Hz
[    19.197] (II) RADEON(0): 640x480@72Hz
[    19.197] (II) RADEON(0): 640x480@75Hz
[    19.197] (II) RADEON(0): 800x600@56Hz
[    19.197] (II) RADEON(0): 800x600@60Hz
[    19.197] (II) RADEON(0): 800x600@72Hz
[    19.197] (II) RADEON(0): 800x600@75Hz
[    19.197] (II) RADEON(0): 832x624@75Hz
[    19.197] (II) RADEON(0): 1024x768@60Hz
[    19.197] (II) RADEON(0): 1024x768@70Hz
[    19.197] (II) RADEON(0): 1024x768@75Hz
[    19.197] (II) RADEON(0): 1280x1024@75Hz
[    19.197] (II) RADEON(0): Manufacturer's mask: 0
[    19.197] (II) RADEON(0): Supported standard timings:
[    19.197] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    19.197] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    19.197] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    19.197] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    19.197] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    19.197] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    19.197] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    19.197] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    19.197] (II) RADEON(0): Supported detailed timing:
[    19.197] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    19.197] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    19.197] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    19.197] (II) RADEON(0): Serial No: 27269
[    19.197] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    19.198] (II) RADEON(0): Monitor name: MD6155AN
[    19.198] (II) RADEON(0): EDID (in hex):
[    19.198] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    19.198] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    19.198] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    19.198] (II) RADEON(0):     4540454a454f302a009851002a403070
[    19.198] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    19.198] (II) RADEON(0):     36390000000000000000000000fd0032
[    19.198] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    19.198] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    19.198] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    19.203] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    19.203] Unhandled monitor type 0
[    19.203] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    19.264] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    19.264] (II) RADEON(0): Using hsync ranges from config file
[    19.264] (II) RADEON(0): Using vrefresh ranges from config file
[    19.264] (II) RADEON(0): Printing DDC gathered Modelines:
[    19.264] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    19.264] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.264] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.264] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    19.264] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    19.264] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    19.264] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.264] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    19.264] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    19.264] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    19.264] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    19.264] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.264] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    19.265] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    19.265] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    19.265] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    19.265] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    19.265] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    19.265] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    19.265] (II) RADEON(0): Year: 2003  Week: 4
[    19.265] (II) RADEON(0): EDID Version: 1.3
[    19.265] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    19.265] (II) RADEON(0): Sync:  Separate
[    19.265] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    19.265] (II) RADEON(0): Gamma: 2.20
[    19.265] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    19.265] (II) RADEON(0): First detailed timing is preferred mode
[    19.265] (II) RADEON(0): GTF timings supported
[    19.265] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    19.265] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    19.265] (II) RADEON(0): Supported established timings:
[    19.265] (II) RADEON(0): 720x400@70Hz
[    19.265] (II) RADEON(0): 640x480@60Hz
[    19.265] (II) RADEON(0): 640x480@67Hz
[    19.265] (II) RADEON(0): 640x480@72Hz
[    19.265] (II) RADEON(0): 640x480@75Hz
[    19.265] (II) RADEON(0): 800x600@56Hz
[    19.265] (II) RADEON(0): 800x600@60Hz
[    19.265] (II) RADEON(0): 800x600@72Hz
[    19.265] (II) RADEON(0): 800x600@75Hz
[    19.265] (II) RADEON(0): 832x624@75Hz
[    19.265] (II) RADEON(0): 1024x768@60Hz
[    19.265] (II) RADEON(0): 1024x768@70Hz
[    19.266] (II) RADEON(0): 1024x768@75Hz
[    19.266] (II) RADEON(0): 1280x1024@75Hz
[    19.266] (II) RADEON(0): Manufacturer's mask: 0
[    19.266] (II) RADEON(0): Supported standard timings:
[    19.266] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    19.266] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    19.266] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    19.266] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    19.266] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    19.266] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    19.266] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    19.266] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    19.266] (II) RADEON(0): Supported detailed timing:
[    19.266] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    19.266] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    19.266] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    19.266] (II) RADEON(0): Serial No: 27269
[    19.266] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    19.266] (II) RADEON(0): Monitor name: MD6155AN
[    19.266] (II) RADEON(0): EDID (in hex):
[    19.266] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    19.266] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    19.266] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    19.266] (II) RADEON(0):     4540454a454f302a009851002a403070
[    19.266] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    19.266] (II) RADEON(0):     36390000000000000000000000fd0032
[    19.266] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    19.266] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    19.266] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    19.272] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    19.272] Unhandled monitor type 0
[    19.272] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    35.243] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    35.243] (II) RADEON(0): Using hsync ranges from config file
[    35.243] (II) RADEON(0): Using vrefresh ranges from config file
[    35.243] (II) RADEON(0): Printing DDC gathered Modelines:
[    35.243] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.243] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.243] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    35.243] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    35.243] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    35.243] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    35.243] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.243] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    35.243] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    35.243] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    35.243] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    35.243] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.243] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    35.243] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    35.243] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    35.243] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    35.243] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    35.244] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    35.244] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    35.244] (II) RADEON(0): Year: 2003  Week: 4
[    35.244] (II) RADEON(0): EDID Version: 1.3
[    35.244] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    35.244] (II) RADEON(0): Sync:  Separate
[    35.244] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    35.244] (II) RADEON(0): Gamma: 2.20
[    35.244] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    35.244] (II) RADEON(0): First detailed timing is preferred mode
[    35.244] (II) RADEON(0): GTF timings supported
[    35.244] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    35.244] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    35.244] (II) RADEON(0): Supported established timings:
[    35.244] (II) RADEON(0): 720x400@70Hz
[    35.244] (II) RADEON(0): 640x480@60Hz
[    35.244] (II) RADEON(0): 640x480@67Hz
[    35.244] (II) RADEON(0): 640x480@72Hz
[    35.244] (II) RADEON(0): 640x480@75Hz
[    35.244] (II) RADEON(0): 800x600@56Hz
[    35.244] (II) RADEON(0): 800x600@60Hz
[    35.244] (II) RADEON(0): 800x600@72Hz
[    35.244] (II) RADEON(0): 800x600@75Hz
[    35.244] (II) RADEON(0): 832x624@75Hz
[    35.244] (II) RADEON(0): 1024x768@60Hz
[    35.244] (II) RADEON(0): 1024x768@70Hz
[    35.244] (II) RADEON(0): 1024x768@75Hz
[    35.244] (II) RADEON(0): 1280x1024@75Hz
[    35.244] (II) RADEON(0): Manufacturer's mask: 0
[    35.244] (II) RADEON(0): Supported standard timings:
[    35.245] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    35.245] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    35.245] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    35.245] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    35.245] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    35.245] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    35.245] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    35.245] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    35.245] (II) RADEON(0): Supported detailed timing:
[    35.245] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    35.245] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    35.245] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    35.245] (II) RADEON(0): Serial No: 27269
[    35.245] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    35.245] (II) RADEON(0): Monitor name: MD6155AN
[    35.245] (II) RADEON(0): EDID (in hex):
[    35.245] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    35.245] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    35.245] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    35.245] (II) RADEON(0):     4540454a454f302a009851002a403070
[    35.245] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    35.245] (II) RADEON(0):     36390000000000000000000000fd0032
[    35.245] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    35.245] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    35.245] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    35.250] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    35.250] Unhandled monitor type 0
[    35.251] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    35.309] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    35.309] (II) RADEON(0): Using hsync ranges from config file
[    35.309] (II) RADEON(0): Using vrefresh ranges from config file
[    35.309] (II) RADEON(0): Printing DDC gathered Modelines:
[    35.309] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.309] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.309] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    35.309] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    35.309] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    35.309] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    35.310] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.310] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    35.310] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    35.310] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    35.310] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    35.310] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.310] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    35.310] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    35.310] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    35.310] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    35.310] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    35.310] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    35.310] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    35.310] (II) RADEON(0): Year: 2003  Week: 4
[    35.310] (II) RADEON(0): EDID Version: 1.3
[    35.310] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    35.310] (II) RADEON(0): Sync:  Separate
[    35.310] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    35.310] (II) RADEON(0): Gamma: 2.20
[    35.310] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    35.310] (II) RADEON(0): First detailed timing is preferred mode
[    35.310] (II) RADEON(0): GTF timings supported
[    35.310] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    35.310] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    35.310] (II) RADEON(0): Supported established timings:
[    35.311] (II) RADEON(0): 720x400@70Hz
[    35.311] (II) RADEON(0): 640x480@60Hz
[    35.311] (II) RADEON(0): 640x480@67Hz
[    35.311] (II) RADEON(0): 640x480@72Hz
[    35.311] (II) RADEON(0): 640x480@75Hz
[    35.311] (II) RADEON(0): 800x600@56Hz
[    35.311] (II) RADEON(0): 800x600@60Hz
[    35.311] (II) RADEON(0): 800x600@72Hz
[    35.311] (II) RADEON(0): 800x600@75Hz
[    35.311] (II) RADEON(0): 832x624@75Hz
[    35.311] (II) RADEON(0): 1024x768@60Hz
[    35.311] (II) RADEON(0): 1024x768@70Hz
[    35.311] (II) RADEON(0): 1024x768@75Hz
[    35.311] (II) RADEON(0): 1280x1024@75Hz
[    35.311] (II) RADEON(0): Manufacturer's mask: 0
[    35.311] (II) RADEON(0): Supported standard timings:
[    35.311] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    35.311] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    35.311] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    35.311] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    35.311] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    35.311] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    35.311] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    35.311] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    35.311] (II) RADEON(0): Supported detailed timing:
[    35.311] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    35.311] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    35.311] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    35.311] (II) RADEON(0): Serial No: 27269
[    35.311] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    35.311] (II) RADEON(0): Monitor name: MD6155AN
[    35.311] (II) RADEON(0): EDID (in hex):
[    35.311] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    35.311] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    35.311] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    35.311] (II) RADEON(0):     4540454a454f302a009851002a403070
[    35.312] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    35.312] (II) RADEON(0):     36390000000000000000000000fd0032
[    35.312] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    35.312] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    35.312] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    35.317] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    35.317] Unhandled monitor type 0
[    35.317] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    35.377] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    35.377] (II) RADEON(0): Using hsync ranges from config file
[    35.377] (II) RADEON(0): Using vrefresh ranges from config file
[    35.377] (II) RADEON(0): Printing DDC gathered Modelines:
[    35.377] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    35.377] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.377] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    35.377] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    35.377] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    35.378] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    35.378] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.378] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    35.378] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    35.378] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    35.378] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    35.378] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.378] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    35.378] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    35.378] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    35.378] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    35.378] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    35.378] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    35.378] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    35.378] (II) RADEON(0): Year: 2003  Week: 4
[    35.378] (II) RADEON(0): EDID Version: 1.3
[    35.378] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    35.378] (II) RADEON(0): Sync:  Separate
[    35.378] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    35.378] (II) RADEON(0): Gamma: 2.20
[    35.378] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    35.378] (II) RADEON(0): First detailed timing is preferred mode
[    35.378] (II) RADEON(0): GTF timings supported
[    35.378] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    35.378] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    35.379] (II) RADEON(0): Supported established timings:
[    35.379] (II) RADEON(0): 720x400@70Hz
[    35.379] (II) RADEON(0): 640x480@60Hz
[    35.379] (II) RADEON(0): 640x480@67Hz
[    35.379] (II) RADEON(0): 640x480@72Hz
[    35.379] (II) RADEON(0): 640x480@75Hz
[    35.379] (II) RADEON(0): 800x600@56Hz
[    35.379] (II) RADEON(0): 800x600@60Hz
[    35.379] (II) RADEON(0): 800x600@72Hz
[    35.379] (II) RADEON(0): 800x600@75Hz
[    35.379] (II) RADEON(0): 832x624@75Hz
[    35.379] (II) RADEON(0): 1024x768@60Hz
[    35.379] (II) RADEON(0): 1024x768@70Hz
[    35.379] (II) RADEON(0): 1024x768@75Hz
[    35.379] (II) RADEON(0): 1280x1024@75Hz
[    35.379] (II) RADEON(0): Manufacturer's mask: 0
[    35.379] (II) RADEON(0): Supported standard timings:
[    35.379] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    35.379] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    35.379] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    35.379] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    35.379] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    35.379] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    35.379] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    35.379] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    35.379] (II) RADEON(0): Supported detailed timing:
[    35.379] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    35.379] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    35.379] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    35.379] (II) RADEON(0): Serial No: 27269
[    35.379] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    35.379] (II) RADEON(0): Monitor name: MD6155AN
[    35.379] (II) RADEON(0): EDID (in hex):
[    35.379] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    35.379] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    35.379] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    35.380] (II) RADEON(0):     4540454a454f302a009851002a403070
[    35.380] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    35.380] (II) RADEON(0):     36390000000000000000000000fd0032
[    35.380] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    35.380] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    35.380] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    35.385] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    35.385] Unhandled monitor type 0
[    35.385] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[    42.356] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    42.356] (II) RADEON(0): Using hsync ranges from config file
[    42.356] (II) RADEON(0): Using vrefresh ranges from config file
[    42.356] (II) RADEON(0): Printing DDC gathered Modelines:
[    42.356] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    42.356] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    42.356] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    42.356] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    42.356] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    42.356] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    42.356] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    42.356] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    42.356] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    42.356] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    42.356] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    42.356] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    42.357] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    42.357] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    42.357] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    42.357] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[    42.357] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[    42.357] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[    42.357] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[    42.357] (II) RADEON(0): Year: 2003  Week: 4
[    42.357] (II) RADEON(0): EDID Version: 1.3
[    42.357] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    42.357] (II) RADEON(0): Sync:  Separate
[    42.357] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    42.357] (II) RADEON(0): Gamma: 2.20
[    42.357] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    42.360] (II) RADEON(0): First detailed timing is preferred mode
[    42.360] (II) RADEON(0): GTF timings supported
[    42.360] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[    42.360] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[    42.360] (II) RADEON(0): Supported established timings:
[    42.360] (II) RADEON(0): 720x400@70Hz
[    42.360] (II) RADEON(0): 640x480@60Hz
[    42.360] (II) RADEON(0): 640x480@67Hz
[    42.360] (II) RADEON(0): 640x480@72Hz
[    42.361] (II) RADEON(0): 640x480@75Hz
[    42.361] (II) RADEON(0): 800x600@56Hz
[    42.361] (II) RADEON(0): 800x600@60Hz
[    42.361] (II) RADEON(0): 800x600@72Hz
[    42.361] (II) RADEON(0): 800x600@75Hz
[    42.361] (II) RADEON(0): 832x624@75Hz
[    42.361] (II) RADEON(0): 1024x768@60Hz
[    42.361] (II) RADEON(0): 1024x768@70Hz
[    42.361] (II) RADEON(0): 1024x768@75Hz
[    42.361] (II) RADEON(0): 1280x1024@75Hz
[    42.361] (II) RADEON(0): Manufacturer's mask: 0
[    42.361] (II) RADEON(0): Supported standard timings:
[    42.361] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    42.361] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    42.361] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    42.361] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[    42.361] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[    42.361] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    42.361] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[    42.361] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[    42.361] (II) RADEON(0): Supported detailed timing:
[    42.361] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    42.361] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    42.361] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    42.361] (II) RADEON(0): Serial No: 27269
[    42.361] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[    42.361] (II) RADEON(0): Monitor name: MD6155AN
[    42.361] (II) RADEON(0): EDID (in hex):
[    42.361] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[    42.362] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[    42.362] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[    42.362] (II) RADEON(0):     4540454a454f302a009851002a403070
[    42.362] (II) RADEON(0):     1300520e1100001e000000ff00323732
[    42.362] (II) RADEON(0):     36390000000000000000000000fd0032
[    42.362] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[    42.362] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[    42.362] (II) RADEON(0): EDID vendor "MED", prod id 18272
[    42.367] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    42.367] Unhandled monitor type 0
[    42.367] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[   731.640] (II) RADEON(0): EDID vendor "MED", prod id 18272
[   731.641] (II) RADEON(0): Using hsync ranges from config file
[   731.641] (II) RADEON(0): Using vrefresh ranges from config file
[   731.641] (II) RADEON(0): Printing DDC gathered Modelines:
[   731.641] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   731.641] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   731.641] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   731.641] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   731.641] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   731.641] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   731.641] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   731.641] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   731.641] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   731.641] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   731.641] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   731.641] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   731.642] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   731.642] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   731.642] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   731.642] (II) RADEON(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 -hsync +vsync (43.8 kHz)
[   731.642] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 1
[   731.642] (II) RADEON(0): EDID data from the display on output: VGA-0 ----------------------
[   731.642] (II) RADEON(0): Manufacturer: MED  Model: 4760  Serial#: 38267
[   731.642] (II) RADEON(0): Year: 2003  Week: 4
[   731.642] (II) RADEON(0): EDID Version: 1.3
[   731.642] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[   731.642] (II) RADEON(0): Sync:  Separate
[   731.642] (II) RADEON(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[   731.642] (II) RADEON(0): Gamma: 2.20
[   731.642] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   731.642] (II) RADEON(0): First detailed timing is preferred mode
[   731.642] (II) RADEON(0): GTF timings supported
[   731.642] (II) RADEON(0): redX: 0.631 redY: 0.354   greenX: 0.294 greenY: 0.596
[   731.642] (II) RADEON(0): blueX: 0.143 blueY: 0.087   whiteX: 0.300 whiteY: 0.340
[   731.642] (II) RADEON(0): Supported established timings:
[   731.642] (II) RADEON(0): 720x400@70Hz
[   731.643] (II) RADEON(0): 640x480@60Hz
[   731.643] (II) RADEON(0): 640x480@67Hz
[   731.643] (II) RADEON(0): 640x480@72Hz
[   731.643] (II) RADEON(0): 640x480@75Hz
[   731.643] (II) RADEON(0): 800x600@56Hz
[   731.643] (II) RADEON(0): 800x600@60Hz
[   731.643] (II) RADEON(0): 800x600@72Hz
[   731.643] (II) RADEON(0): 800x600@75Hz
[   731.643] (II) RADEON(0): 832x624@75Hz
[   731.643] (II) RADEON(0): 1024x768@60Hz
[   731.643] (II) RADEON(0): 1024x768@70Hz
[   731.643] (II) RADEON(0): 1024x768@75Hz
[   731.643] (II) RADEON(0): 1280x1024@75Hz
[   731.643] (II) RADEON(0): Manufacturer's mask: 0
[   731.643] (II) RADEON(0): Supported standard timings:
[   731.643] (II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   731.643] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[   731.643] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[   731.643] (II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 70  vid: 19041
[   731.643] (II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[   731.643] (II) RADEON(0): #5: hsize: 800  vsize 600  refresh: 60  vid: 16453
[   731.643] (II) RADEON(0): #6: hsize: 800  vsize 600  refresh: 70  vid: 19013
[   731.643] (II) RADEON(0): #7: hsize: 800  vsize 600  refresh: 75  vid: 20293
[   731.643] (II) RADEON(0): Supported detailed timing:
[   731.643] (II) RADEON(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[   731.643] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[   731.644] (II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[   731.644] (II) RADEON(0): Serial No: 27269
[   731.644] (II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 82 kHz, PixClock max 140 MHz
[   731.644] (II) RADEON(0): Monitor name: MD6155AN
[   731.644] (II) RADEON(0): EDID (in hex):
[   731.644] (II) RADEON(0):     00ffffffffffff0034a460477b950000
[   731.644] (II) RADEON(0):     040d010368221b78eba69ca15a4b9824
[   731.644] (II) RADEON(0):     164c57bfef008180818f6140614a614f
[   731.644] (II) RADEON(0):     4540454a454f302a009851002a403070
[   731.644] (II) RADEON(0):     1300520e1100001e000000ff00323732
[   731.644] (II) RADEON(0):     36390000000000000000000000fd0032
[   731.644] (II) RADEON(0):     4b1e520e000a202020202020000000fc
[   731.644] (II) RADEON(0):     004d4436313535414e0a2020202000c9
[   731.644] (II) RADEON(0): EDID vendor "MED", prod id 18272
[   731.650] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[   731.650] Unhandled monitor type 0
[   731.650] (II) RADEON(0): Output: S-video, Detected Monitor Type: 0
[  1357.918] (II) XKB: reuse xkmfile /var/lib/xkb/server-0A9273296DC6E38A842862A802EBD5BDC6E7DEBF.xkm


```#########################

As for the rest, lucid looks great... :) 


Harry

---

### Post by dirty_harry on 2010-08-22
bought a geforce...

should solve the case.

---

