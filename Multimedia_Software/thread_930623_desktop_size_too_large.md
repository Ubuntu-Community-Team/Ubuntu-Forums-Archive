---
title: "desktop size too large"
date: 2008-09-26
forum: Multimedia Software
---

### Post by vong on 2008-09-26
I have installed the new 6.04 64 bit version of kubuntu and all is working.. for the most part.  My desktop is larger then my screen by about a centimetre all around (the edge of the desktop is about a cm past the edge of the screen by about 1cm)

Hardware Specs:

I have a 42 inch Sharp Aquos HD lcd tv as my monitor ([http://www.sharp.ca/products/index.asp?cat=30&id=717](http://www.sharp.ca/products/index.asp?cat=30&id=717))

nVidia GeForce 8500 GT using the nvidia binary installed via aptitude.

I have done much research about the problem and I think the only solution is to shrink the view port manually in the xorg.conf file (seen below for current).  I am running the full 1920x1080 resolution, but the problem appears at all resolutions.  Is this the only solution, or is there another way.  If so some help with what needs to be done to my xorg would be much appreciated.

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

Thanks in advance :)

---

