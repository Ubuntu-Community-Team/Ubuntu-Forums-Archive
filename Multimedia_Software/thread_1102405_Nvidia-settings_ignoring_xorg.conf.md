---
title: "Nvidia-settings ignoring xorg.conf?"
date: 2009-03-21
forum: Multimedia Software
---

### Post by Alarindris on 2009-03-21
Been struggling with this for 2 days now.

The max size for my monitor is 1280x1024 according to the documentation.  However, nvidia-settings will only let it go to 1152x864.

I've tried adding resolutions to the screen section in xorg.conf, but it's just being ignored.

I've done everything I can think of, even reinstalled my nvidia drivers and no luck.

Looking to at least be pointed in the right direction.

Heres xorg:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GTS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024 +0+0"
    Option         "ModeValidation" "DFP-0: NoDFPNativeResolutionCheck,NoMaxPClkCheck"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection
```

I don't see how it would do anything other than 1280x1024.  Any help much appreciated.

---

### Post by inobe on 2009-03-21
don't know what's up with that' why not try in nvidia settings under resolution ?

```
gksu nvidia-settings
```

---

### Post by Alarindris on 2009-03-21
That's exactly the problem, 1280x1024 is not listed as an option.

---

### Post by inobe on 2009-03-21
i found this

> Update 2
--------

I have a fully working twinhead (dual monitor) configuration with two
LCD monitors which are not identical in size. I was able to get it
working with help from the good documentation provided with the closed
source nvidia drivers which I installed from the fantastic Livna
repository. The config below also includes a work-around for max
resolution with the Acer AL2216W. The key issue of the work around was
getting X and nvidia to ignore the (apparently) incorrect info from
probing the monitor. This is what I did:

Section "Screen"
...
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: 1680x1050 +1280+0"
    Option         "ModeValidation" "DFP-0: NoDFPNativeResolutionCheck,NoMaxPClkCheck"
...
EndSection



[http://defindit.com/readme_files/x_windows_dual_monitor.html](http://defindit.com/readme_files/x_windows_dual_monitor.html)


ignore the dual head stuff, you may be able to use this information.

---

### Post by doas777 on 2009-03-21
I've usually found that when an xorg option is ignored, that it is either malformed (typos) or that the setting is not supported.

I had an geforce 8500 once and had horrible overscan. nvidia-settings did not have a overscan controler, so I put it in by hand. no love. it appears that that card with that driver would never be able to workout.

---

### Post by tommcd on 2009-03-22
Just checking, but are the horizontal sync and vertical refresh rates listed in your xorg.conf correct for your monitor? With older versions of xorg I had sometimes found that getting 1280x1024 was impossible until I set the horizontal and vertical refresh rates correctly in xorg.conf.

---

### Post by Alarindris on 2009-03-22
Thanks for the replies.

Tried inobe's suggestion, I actually looked at that page earlier and got that line in xorg (i forgot to change DFP to CRT, but even when I changed it, it still didn't work).

As far as the refresh rate, I have no idea what they should be.  I've got no manual for my monitor.  Its an emachine e17t4 and I can find any info on it.  I ran edid and it said it had invalid information or something like that.

Why should this be so difficult?

---

### Post by inobe on 2009-03-22
it has to be something simple......

the monitor i had in the past had a stupid reset button that !

maybe when it's probed it sees the modified settings..


idk, you never know' but then i had those old crt's whistle at me using incorrect settings "overclock a crt lols"

---

### Post by Alarindris on 2009-03-24
bump

---

### Post by tommcd on 2009-03-25
Try using **xrandr** to set your proper screen resolution. The xrandr utility has replaced the old tried and true 'dpkg-reconfigure xserver-xorg' as the way to fix xorg problems. See this tutorial:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Sorry I didn't think of it earlier. Hope this works for you.

---

