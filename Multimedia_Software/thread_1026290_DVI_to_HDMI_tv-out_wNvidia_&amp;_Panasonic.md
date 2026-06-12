---
title: "DVI to HDMI tv-out w/Nvidia &amp; Panasonic"
date: 2008-12-31
forum: Multimedia Software
---

### Post by gr3gg0r on 2008-12-31
I have a Panasonic HDTV (TH-42PZ85U A) and an Nvidia Geforce 8800gt.  I have a dvi to hdmi cable, but whenever I connect it, nothing is ever output to the tv.  Ubuntu recognizes the tv as a panasonic and detects all supported resolutions up to 1920 x 1080, but for the life of me, I can't get a picture to output to the screen.  I've tried it on two computers running ubuntu and one mac all with the same results.  The other ubuntu computer has a geforce 8400gs i believe.

I'm wondering if it could be the cable, but the computers all detect the tv and as far as I can tell, the computer thinks it is successfully outputing a singnal to the tv.  But the tv doesn't seem to see it.

Any thoughts would be great.  Here's my xorg.conf

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ACI ASUS VW223"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
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
    BoardName      "GeForce 8800 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by wackston on 2009-01-03
Hmmm... a cable problem would be unusual.  However, to "recognise" the attached monitor only the DDC/CI channels I2C interface needs to work across the cable - just two pins and a very robust/slow signalling scheme...

More likely: some Twinview confusion or a TV that with bogus EDID data or similar confusing things.  Have you tried attaching the TV as the *only* monitor at 720p to give a super-conservative "baseline" to work from?

What does your Xorg.0.log say?

---

### Post by Cyr1dian on 2009-07-01
I have practically the same problem with Panasonic TH-42PZ81E. I'm trying to use my laptops HDMI out but to no avail. I know my laptop and cable are OK because it with Vista (yes I found something in Vista that worked - after tweaking it).

I am using the NVidia X server graphical tool to set everything up. I am able to use the TV's VGA in and I can also use my laptop with an external 19" monitor (again VGA).

So something seems to be up with HDMI out, I wonder if it is specific to Nvidia, Panasonic Plasma TVs or the combination of the two. Although I cannot imagine the TV being a factor.

Using a fully patched Jackalope.

Any insights anyone?

---

### Post by gr3gg0r on 2009-07-02
Well I got the problem solved.  It was simply a bad cable.  I got a new cable and everything works great now. :guitar:

---

