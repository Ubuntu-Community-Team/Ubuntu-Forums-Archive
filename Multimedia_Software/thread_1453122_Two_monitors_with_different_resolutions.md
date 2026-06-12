---
title: "Two monitors with different resolutions"
date: 2010-04-12
forum: Multimedia Software
---

### Post by allenck on 2010-04-12
I am running Ubuntu 9.10 on an HP laptop with an Intel 82852/82855 GM/GMC Graphics controller. I have a 2nd monitor attached to the VGA port (HP f1703). The problem is that the two screens have different resolutions. the laptop is 1280 x 768 and the other monitor is 1280 x 1024. The xorg.conf file that was created with Xorg -config set both monitors up with 1280 x 1024 resolution so my screen on the laptop looks all "squashed". I have tried to reconfigure it using the Display Preferences dialog but after i re-boot, both screens are unviewable and I have to restore my previous xorg.conf file. I went through the **HOWTO: Jaunty Intel Graphics Performance Guide **procedure to setup a "safe" configuration but didn't work and I had to restore my "good' xorg.conf file. 

What do I need to do to setup my two screens with the correct resolutions: 1280 x 768 and 1280 x 1024? 

Here is the video portion from my "good" xorg.conf file 
Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82852/855GM Integrated Graphics Device"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card1"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82852/855GM Integrated Graphics Device"
    BusID       "PCI:0:2:1"
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

---

### Post by kendoori on 2010-04-13
I have a similar setup. I use my laptop's default screen as a secondary monitor @ 1024x768, and have a wide screen monitor that I use as the main screen (1920x1200). I have an Intel GM965 video card. As I recall under 9.10 both screens were recognized properly. There are a couple of good gui apps in the repositories that helped me. One is called LXRandR, the other is call grandr. Both will give you pretty granular control over each monitor separately. I have found that once you get it set, it works properly.

I actually don't appear to have an a xorg.conf file

---

