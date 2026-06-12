---
title: "can't enable visual effect"
date: 2012-01-06
forum: Multimedia Software
---

### Post by vaah on 2012-01-06
Hi, I don't know when this has started but at the moment my ubuntu 10.10 can't enable visual effect. hence losing compiz effect. I have radeon 2400xt. Here is the output of lspci:

```
$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV610 [Radeon HD 2400 XT] [1002:94c1]

```

I tried activate the recommended driver through System->administration->additional drivers and the result is my rig won't display the proper resolution (supposed to be 1680x1050). So I remove the driver and install the proprietary driver downloaded from amd website. The result still the same, I still can't enable visual effect. although the display resolution is correct.

What am I Supposed to do? Please help me guys.

---

### Post by bluexrider on 2012-01-06
Once your drivers are installed you may need to reconfigure your Xorg.

Here is a wiki  [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

### Post by vaah on 2012-01-06
I'm sorry i'm completely lost. what am i supposed to do?
This is my xorg.conf
```

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by vaah on 2012-01-08
bump my thread. anyone can help?

---

### Post by vaah on 2012-01-15
Hi Guys, I wanna report back, I just found out that the culprit causing me trouble enabling visual in visual effect tabs!! It's the setting in bios, i set option Enable onboard VGA automatically. It should be set disable. Voila! it works now.
Phew, I didn't know having cutting edge rig would be this much trouble LOL.

btw, my system is sandy bridge, maybe this issue only happens in ubutnu 10.10 with kernel 2.6.35-31...Problem solve for now! :)

---

