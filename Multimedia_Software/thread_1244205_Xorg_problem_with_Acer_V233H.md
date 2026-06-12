---
title: "Xorg problem with Acer V233H"
date: 2009-08-19
forum: Multimedia Software
---

### Post by webkage on 2009-08-19
I have tried many combinations of xorg configuration with my Acer V233H, my graphic card is a Nvidia GeForce 8500 GT with the last propietaries drivers, the 180 version and running ubuntu 9.04 64bits

In the manual specified that H and V are 54.2-83.8 and 49-75 but I tried several time and went I reboot the screen stays black after the GRUB and since the ubuntu logo progress bar.

This is the current state of the xorg with only allow me to set resolution up to 1360x768 , (in Windows is working with 1920x1080, 1680x1050, 1600x1200, 1440x900 and so on, no problem of hardware them):

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

And I try to change adding to something like this:

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    DefaultDepth 24
    Depth 16
    Modes "1680x1050" "1600x1200" "1440x900" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
    Depth 24
    Modes "1680x1050" "1600x1200" "1440x900" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    EndSection

also doing the H and V thing, running a lot of command like  sudo reconfigure-dpkg but only promp question about the keyboard and not the monitor. Also tried some lives version and try to copy the xorg from there but all has the same problem

Anyone who has the same/similar monitor can copypaste his/her own xorg file please? or give news ideas how to continue because I am lost :confused:

---

### Post by webkage on 2009-08-23
Just updating, I also tried deleting the xorg and sudo nvidia-xconfig and also installing Ubuntu 8.10 with the 177 and 173 drivers, didn't work neither.

In Windows when working at 1920x1080 the display menu says H:67 and V:60, I tried to specified that in the xorg but I am suppose to write a range not single values. Are anything similar in Windows like xorg from where I can copy the actual working values or something? I will try a little more and if nothing work try to change in the store for other model because this is a pain in the neck :-S

---

