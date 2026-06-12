---
title: "Mythbuntu login problem since 9.10"
date: 2010-03-03
forum: Mythbuntu
---

### Post by mathy on 2010-03-03
Hello All, 

I am running mythbuntu since quite some time on a frontend only computer... since updating to 9.10 I have a problem with the login. 

So what happens very often (but not always) is that the system boots, tries to do auto-login, but X only starts (screen flashes to black) and then crashes (?), gdm is reloaded and the login screen is displayed again. 

Then I try to login manually, and very often then it will log in and start the frontend, sometimes I have to try to login several times until it works. It seems that once it has logged in OK, restarting GDM always will auto-login ok again.

My hardware is a Dual Core Pentium with an NVIDIA NVS 290 PCIe graphics board, running the binary driver (happens with both mythbuntu driver packages and newest drivers directly from NVidia). I have a remote back end and as hard disk I use a combination of a 2GB CF card in a CF-SATA adaptor for root plus two 1GB USB sticks for some sub directories of root. That seems to work nicely. The system has 1GB of RAM, no swap (enough for myth frontend, more than 600k free when running). 

When I look at XOrg.0.log, when login worked OK and the frontend is running, the last line will be: 

(II) NVIDIA(0): Setting mode "1440x900"

If the login failed, after that line I will find: 

(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) ABBAHOME: Close
(II) UnloadModule: "evdev"
(II) ABBAHOME: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

I would appreciate any hint on how to solve this!

Thanks and cheers, 

Matthias

---

### Post by neutron68 on 2010-03-03
This is a known bug in 9.10.  You must have missed the other forum posts when you searched the forum for the problem.

Thus far, the bug has not been closed out (not solved officially):
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/463314](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/463314)

I found a solution on my machine back in November 2009.  It involved editing the xorg.conf file.

see:
[http://ubuntuforums.org/showthread.php?p=8322246](http://ubuntuforums.org/showthread.php?p=8322246)

---

### Post by mathy on 2010-03-09
Hi Neutron, 

thanks for the hint - you are right pointing me to the search function... I had googled but not used the search of the forum. 

In the end it seems to work now for me, too. :popcorn: I think it worked after inserting the "composite" "disabled" option in xorg.conf. Considering the many different approaches to fix this, I am not sure that the composite option actually is a problem... changing it seems to trigger a behaviour change somewhere. 

Thanks again for your help

Matthias

---

### Post by neutron68 on 2010-03-09
I'm glad you got it working.  I'm interested in seeing what your working xorg.conf file looks like, if you care to share it.

Cheers!
Eric

---

### Post by mathy on 2010-03-11
Hi Eric, 

sure I can post my xorg.conf. 

It is remarkable that my system also switches to a screen resolution of 1440x900 like varingo's system. It is already quite some time ago, but iirc I would think that like him, I set this resolution in nvidia-settings, it gives good results, as at the time being, I do not have HD programming available (have to get a new vdpau capabble video card first).

So here is my xorg.conf: 
```


Section "ServerLayout"

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Mouse0" "CorePointer"
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
    ModelName      "Acer X243HQ"
    HorizSync       30.0 - 80.0
    VertRefresh     55.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 290"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "UseEvents" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

Cheers, 

Matthias

---

