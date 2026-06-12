---
title: "Need help setting up dual spaned monitors"
date: 2008-06-06
forum: Multimedia Software
---

### Post by wetjet on 2008-06-06
I just installed ubuntu 8.04. I have 2 pci express video cards. One is a geforce 7950 gx2, the other is a geforce 7600 gt. Both LCD's are 20.1" widescreen viewsonics with 1680x1050 resolution. One is a VX2025WM, the other is a VG2030WM.

I have a basic, defaul xorg.conf file. The Geforce 7950 GX2 is currently working fine at the proper resolution on the VX2025WM.  There are 2 DVI ports in the back of the 7950 GX2, but I'd like to use 2 video cards to make this happen, as I dual boot xp and xp for some reason doesn't like me to span my display on one card.... anyways.

Here is my current xorg.conf...

> Section "InputDevice"
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


I'm not sure if you need the pci bus that the video cards are on, so I'll state them here.  The 7950 gx2 is on 3:0:0 and 4:0:0 (dual gpu card).  The 7600 GT is on 7:0:0

Other than that, is there anything else that may help with my xorg.conf?

Thank you.

---

### Post by Pjotr123 on 2008-06-06
I suggest you try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

That will probably do the job.  :-)

Greeting, Pjotr.

---

