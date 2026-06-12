---
title: "Help installing ATI radeon 9250 video card"
date: 2010-05-19
forum: Multimedia Software
---

### Post by CheAmr on 2010-05-19
Hello
I have 128MB video card ATI radeon 9250A 

I just installed the 10.04LTS ubuntu and I want to install my video card on it 

any help ? 

Thanks

---

### Post by I8NY on 2010-05-19
go to System>Administrative>Hardware Drivers, it will then search for video card drivers and list one if your card is supported.  If your card is not listed then you can't do any 3D games, ATI doesn't like to support old hardware on linux.

---

### Post by CheAmr on 2010-05-19
> **I8NY said:**
> go to System>Administrative>Hardware Drivers, it will then search for video card drivers and list one if your card is supported.  If your card is not listed then you can't do any 3D games, ATI doesn't like to support old hardware on linux.
my card isn't listed , 
any trick or something to make it work ?

---

### Post by Yellow Pasque on 2010-05-19
The open-source drivers are pre-installed. Proprietary drivers are not available for older cards.

---

### Post by CheAmr on 2010-05-19
I installed it on the ex ubuntu , but i dont remember how I've done it 
so please I'm sure there is a way , 
help me guys :)

---

### Post by Yellow Pasque on 2010-05-19
Your video card is installed. You don't need to do anything.

---

### Post by hsoulen on 2010-05-20
> **Temüjin said:**
> Your video card is installed. You don't need to do anything.

100% Correct.

Please see this thread: [http://ubuntuforums.org/showthread.php?p=9199177](http://ubuntuforums.org/showthread.php?p=9199177)

The Open Source driver installed by default should be all you need.

Cheers,

Hank

---

### Post by CheAmr on 2010-05-20
why ubuntu is slow then ? 
although on windows its pretty faster

---

### Post by hsoulen on 2010-05-20
> **CheAmr said:**
> why ubuntu is slow then ? 
although on windows its pretty faster

Not so quick answer is that AMD/ATI do not support their older hardware through a "proprietary" driver, only the newer hardware.

The only drivers available for "legacy" ATI hardware is through the Open Source driver included in Ubuntu (and most other distros), although the folks who develop these drivers do an amazing job, they are not necessarily privy to all the special functions and acceleration that the folks who make the hardware are.

What this all means is that your card will most likely always work better with drivers directly from ATI (I think the Catalyst drivers from ATI still support this card for Windows but I don't have one so I am not sure) but those are not available for Linux for older card models.

This being said, the Open Source drivers for ATI as far as I know (I run NVidia) are pretty good even for older hardware, and some folks wont even install any non-Open Source software so they run these drivers even on newer cards.

Best bet if you are unhappy with performance but love the Linux is to go out and get a cheaper low/mid-range but new product which would give you better performance even with the Open Source driver.

Good Luck,

Hank

---

### Post by CheAmr on 2010-05-21
Thank you Hank 
I'll do so soon

---

### Post by tome89 on 2010-07-02
Hi

I have an old ATI Radeon 9250 Pro 128 MB.
When I installed Ubuntu Lucid I had too performance issues.
I edited the /etc/X11/xorg.conf and added

```
Option     "ColorTiling"             "on"
```to the device section, it solved my problem (with KMS).

If the screen is black on compiz 3D effects, start CompizConfig, go to General Options->Display Settings and turn off lighting.

Here is my xorg.conf:
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
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "glx"
    Load  "record"
    Load  "extmod"
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
    VendorName   "GSM"
    ModelName    ""
    HorizSync    30.0 - 83.0
    VertRefresh  56.0 - 75.0
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
        Option     "ColorTiling"             "on"    
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
        Option     "ClockGating"            "on"    
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
        Option     "ForceLowPowerMode"      "on"    
        Option     "DynamicPM"              "on"
    Option       "DynamicClocks"        "on"    
        #Option     "NewPLL"                 # [<bool>]
        #Option     "ZaphodHeads"            # <str>
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV280 [Radeon 9200 PRO]"
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
```I hope it will help Radeon9250 users :)
Tom

---

