---
title: "How to add modeline in xorg.conf"
date: 2011-08-13
forum: Multimedia Software
---

### Post by krosswindz on 2011-08-13
I have an apple tv1 running ubuntu hardy. Due to audio video requirements I do not want to upgrade. I am trying to get 1080p24 working my TV. I ran X in verbose mode to ensure that my TV supports 1080p24 and it does.

For some reason the X is not able to see the 1920x1080 @ 24Hz mode. I got the required information to add the modeline to my xorg.conf.

My xorg.conf is as follows

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
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
    Identifier     "Monitor0"
    VendorName     "SNY"
    ModelName      "Sony TV"
    HorizSync       15.0 - 70.0
    VertRefresh     58.0 - 62.0
    Option         "DPMS"
    Modeline       "1920x1080_24" 74.16 1920 2558 2602 2750 1080 1084 1089 1125 +HSync +VSync
EndSection

Section "Device"
    Identifier          "Device0"
    Driver              "nvidia"
    VendorName          "NVIDIA Corporation"
    Option              "NoLogo" "true"
    Option              "RegistryDwords" "RMDisableRenderToSysmem=1"
    Option              "DynamicTwinView" "false"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes       "1920x1080" "1920x1080_60" "1920x1080_60_0" "1920x1080_24"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

When I check the Xorg log file I have the following warning

```

(WW) NVIDIA(0): No valid modes for "1920x1080_24"; removing.

```

Is there any way I can append the valid modeline for 1920x1080 @ 24Hz to. I am avoiding using a modified EDID.

---

### Post by realzippy on 2011-08-13
edit,
BB  already has found solution.

---

### Post by BicyclerBoy on 2011-08-13
1080p24 should be a valid internal (X server) mode .

AppleTV1 uses a nVidia Go7300 & a very low power intel CPU & almost no RAM.
The 7000 family were all pretty useless for video decode.

Your vertfresh info in your monitor section is incompatible with 24p.
So your required mode is not validated & gets chucked out..

Have a read thru' your
/var/log/Xorg.0.log
it should reveal some clues to what is happening

The XBMC forums suggest that AppleTV1 can only manage 720p & post-decode scaling to 1080.
It is suggested that 720p playback is superior.

There are suggestions about using Broadcom CrystalHD but support for this device has stalled.

---

### Post by krosswindz on 2011-08-14
> **BicyclerBoy said:**
> 1080p24 should be a valid internal (X server) mode .

AppleTV1 uses a nVidia Go7300 & a very low power intel CPU & almost no RAM.
The 7000 family were all pretty useless for video decode.

Your vertfresh info in your monitor section is incompatible with 24p.
So your required mode is not validated & gets chucked out..

Have a read thru' your
/var/log/Xorg.0.log
it should reveal some clues to what is happening

The XBMC forums suggest that AppleTV1 can only manage 720p & post-decode scaling to 1080.
It is suggested that 720p playback is superior.

There are suggestions about using Broadcom CrystalHD but support for this device has stalled.

I have a Broadcom CrystalHD in my Apple TV1 for hardware video decoding. I was helped in another forum to use following option

```

Option "ModeValidation" "NoVertRefreshCheck"

```

Now it detects the 24Hz modeline. I know have to figure out how to disable 120Hz to prevent it from using it xbmc.

---

### Post by Royke on 2013-01-13
It may be a good hint to tell @krosswindz that 24Hz viewing would give a terrible headache! Your refreshrate can't be good and xorg knows it..

---

