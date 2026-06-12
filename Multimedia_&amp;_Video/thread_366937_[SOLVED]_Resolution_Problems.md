---
title: "[SOLVED] Resolution Problems"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by borobudur on 2007-02-21
Hi, I have a resolution problem which I can't solve. The highest resolution I can chose is 800x600. Do you think I can install the new nvidia driver. My machine is already  5 years old?

Hier is my xorg.conf datas:

```
Section "Device"
    Identifier    "NVIDIA Corporation NV15DDR [GeForce2 Ti]"
    Driver        "nv"
    BusID        "PCI:1:5:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV15DDR [GeForce2 Ti]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```Thanks guys!

---

### Post by r4ik on 2007-02-21
Install the driver from here,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Then type in a terminal
Code:

sudo nvidia-settings

and set the resolution from there. Then click on "apply" and save your settings

Good luck !

---

### Post by borobudur on 2007-03-09
worked out perfect! 
Thanks for your help.
Regards from Zurich
brobudur

---

### Post by r4ik on 2007-03-09
Thanks for the reply good to hear it worked.

---

