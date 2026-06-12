---
title: "extremely slow video, don't know why!"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by platinum on 2008-03-19
hi.

i've installed ubuntu on many systems, but never on a system that has an intel i815 graphics card.

i know, it sucks, but it should be able to render windows at a decent speed anyway. drawing windows is very slow, and rendering web pages is even slower. and glxgears, don't move at all ;)

i finally convinced my dad to let me put linux on his computer because windows was screwing up so much, and i don't want him to get a bad impression because of some video driver error.

here's the output of my xorg.conf file

"
Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82815 CGC [Chipset Graphics Controll$
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82815 CGC [Chipset Graphics Controll$
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x4$
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection
"

basically, i want video acceleration (as much as the intel i815 will give), and an 800x600 resolution with 75hz refresh. my dad has rather poor vision, and requires low resolution.

thanks all!

---

### Post by platinum on 2008-03-19
oh, and i checked synaptics package manager, and it says the drivers are installed, which i find odd.

---

### Post by platinum on 2008-03-19
oh, and cpu usage is crazy.

---

### Post by PlatinumPlus on 2008-03-28
I have having the same problem on my hp compaq nx9010.
I installed Ubuntu, Kubuntu and Edubuntu and I am getting the same results. Sometimes it starts out okay, then after a few minutes it almost freezes. 

Please let me know if you get a solution.

---

