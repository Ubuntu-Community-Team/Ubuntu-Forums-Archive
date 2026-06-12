---
title: "Desktop effects could not be enabled (Newbie for Ubuntu 9.10)"
date: 2010-05-10
forum: Multimedia Software
---

### Post by Axerated on 2010-05-10
Hi,
I am a newbie on Linux system. I had install ubuntu 9.10 as my OS, but I cant activate my videocard. 

I had tried lshw to detect my videocard as: S3 supersavage IX/C
but stated: this device hasn't been claim

I had checked my Xorg.conf
below what is display:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

I had changed it to the below, but still didnt get it working

Section "ServerLayout"
    Identifier     "single head configuration"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load  "glx"
    Load  "dri"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "LCD Panel 1024x768"
    HorizSync    31.5 - 48.5
    VertRefresh  40.0 - 70.0
    Option        "dpms"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        Option     "NoAccel"                "true"
        #Option     "HWCursor"               # [<bool>]
        #Option     "SWCursor"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
 #       Option     "UseBIOS"                "True"
        #Option     "LCDClock"               # <freq>
        #Option     "ShadowStatus"           # [<bool>]
        #Option     "CrtOnly"                # [<bool>]
        #Option     "TvOn"                   # [<bool>]
        #Option     "PAL"                    # [<bool>]
        #Option     "ForceInit"              # [<bool>]
        #Option     "Overlay"                # [<str>]
        #Option     "TransparencyKey"        # [<str>]
        #Option     "ForceInit"              # [<bool>]
        #Option     "DisableXVMC"            # [<bool>]
        #Option     "DisableTile"            # [<bool>]
        #Option     "DisableCOB"             # [<bool>]
        #Option     "BCIforXv"               # [<bool>]
        #Option     "DVI"                    # [<bool>]
        #Option     "BusType"                # [<str>]
        #Option     "DmaType"                # [<str>]
        #Option     "DmaMode"                # [<str>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>

    Identifier  "Videocard0"
    Driver      "savage"
    VendorName  "Videocard vendor"
    BoardName   "S3 SuperSavage IX/C SDR"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Videocard0"
    Monitor    "Monitor0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     16
        Modes    "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes    "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

#Section "DRI"
#    Group        0
#    Mode         0666
#EndSection

Please help me... thanks

---

### Post by xc3RnbFO8P on 2010-05-10
Did you check,
Administration> Hardware Drivers

---

### Post by Axerated on 2010-05-25
> **Ringi said:**
> Did you check,
Administration> Hardware Drivers
 
Yes, but it's state No proprietary drivers are in use on this system.
And I used Hardware lister in Preferences, It reflect my Video Card as "this device has not been claimed."
 
Please help.
 
AR

---

