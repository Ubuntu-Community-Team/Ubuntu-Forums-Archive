---
title: "DELL ST2310 Monitor DVI-D unrecognized by UBUNTU - EDID checksum is invalid -"
date: 2010-10-01
forum: Multimedia Software
---

### Post by Hanine on 2010-10-01
Hello,
I have got a very frustrating problem.
I am not new to Ubuntu but this time I bit my tongue!

Actually it is a problem related to my graphics card "**Intel 945GM**" , it is a real crap card but it is working fine with Windows XP pro (I use windows just for testing)!

Problem : My monitor** DELL ST2310** would not work under **DVI** mode (only VGA mode is working fine)!
I tested with Kubuntu, Ubuntu (several distos), Fedora 13...
Upon booting, I get this error message :

```
EDID checksum is invalid
remainder 130
```the monitor DVI connection is working perfectly under Windows XP.
This means the Intel 945GM cannot read the EDID hexadecimal data transmitted by the monitor through the DVI connection. Yet, System recognizes the graphic card's DVI-D port but set it as disconnected.

My laptop is a Dell Inspiron 9400
Ubuntu version : 10.04 LTS and 10.10 RC

The first time I decided to buy a wide screen to develop Open source utilities...... :(

 I generated  a  xorg.conf file using : sudo X -configure under recovery mode, and here is what it gives :
---------------------
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
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "glx"
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
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
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
    BusID       "PCI:0:2:0"
    Option         "UseDisplayDevice"         "DFP-0"   # Hanine added this line
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
```

---------------------
While :  ```
sudo ddcprobe
```   gives : 
```
vbe: VESA 3.0 detected.
oem: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r) 82945GM Chipset Family Graphics Controller Hardware Version 0.0
memory: 7872kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: f01b
eisa: DELf01b
serial: 32314c4c
manufacture: 15 2010
input: separate sync, composite sync, sync on green, analog signal.
screensize: 51 29
gamma: 2.200000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@75 Hz (VESA)
ctiming: 1152x864@75
ctiming: 1280x1024@60
ctiming: 1920x1200@60
dtiming: 1920x1080@67
monitorserial: W187R04821LL
monitorname: DELL ST2310
monitorrange: 30-83, 56-76
```


[COLOR=Red]***Please help!!!!!!***[/COLOR]

---

### Post by cjqb on 2010-12-08
Have the same problem in my Inspiron 9400, Intel GM945:

The DVI-D output doesn't work, and this is the Log message:

[  200.590004] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[  200.590007] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  200.590011] <3>01 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590014] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590017] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590020] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590024] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590027] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590030] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590033] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................

---

### Post by Hanine on 2010-12-08
> **cjqb said:**
> Have the same problem in my Inspiron 9400, Intel GM945:

The DVI-D output doesn't work, and this is the Log message:

[  200.590004] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[  200.590007] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[  200.590011] <3>01 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590014] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590017] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590020] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590024] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590027] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590030] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................
[  200.590033] <3>ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff  ................

I am sorry for this!
I launched a bug issue in Launchpad and Kernel and nothing changes! No one in the Ubuntu or Linux world is able to fix the problem!

Actually, it is the Intel Linux driver and DRM Linux Kernel issue!
I have been searching for ages in vain! I made all the tests possible but :(
Intel graphics cards are just not fully supported by Linux distros!

All we can do is get a new computer with ATI or NVIDIA graphics! Otherwise we're doomed!

---

### Post by cjqb on 2010-12-09
Thanks anyway!.....I hope somebody fix this  issue soon.

---

