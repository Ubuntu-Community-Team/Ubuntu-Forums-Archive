---
title: "Low resolution on NVidia MX 400"
date: 2010-02-01
forum: Multimedia Software
---

### Post by tonsil on 2010-02-01
Hello everyone,

I'm an absolute beginner on Linux and I've installed Ubuntu 9.10 just a few days ago. Sadly the last couple of days have been an absolute frustration for me, because I could not set my resolution to 1024x768. I couldn't even start exploring Ubuntu yet.

Here's what happens, and after countless hours spent on these forums I know I'm not alone:

I install Ubuntu. My screen resolution is set to 800x600 automatically. I install Nvidia drivers as suggested by the system. I restart. And the screen resolution drops to 640x480. Going to System->Administration->Nvidia settings I see that only two options of resolution are available to me: 640x480 and 320x240. Going to System->Prefs->Display doesn't help either.

After reading some of the similar posts, I tried editing my xorg.conf. Here's what it looks like unaltered:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

I read in some post that it's not the driver that is the problem, but the monitor needs to be set up. Since monitor is not mentioned in the above xorg.conf, I experimented a bit by adding a few lines, to which Ubuntu did not boot.

I tried gksudo displayconfig-gtk on the terminal. It asks for my password and then it just vanishes. Nothing happens.

I am exhausted by this point. I'm desperately looking for help. I'm using an Nvidia MX400 card and Panasonic PanaSync S70 monitor. Kindly guide me through these steps.

Thank you.

---

### Post by tonsil on 2010-02-01
It works!

It's as I thought. Several lines about monitor have to be added on xorg.conf.
For people who may experience a similar issue here's what I've done:

Section "Monitor"
    Identifier   "Monitor0"
    VendorName     "Unknown"
        ModelName      "CRT-0"
        HorizSync       30.0 - 70.0
        VertRefresh     50.0 - 180.0
        Option         "DPMS"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "Screen"
    Identifier    "Default Screen"
        Device "Default Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
    Monitor         "Monitor0"
    SubSection     "Display"
    Depth       24
    Modes     "1024x768" "800x600"
        EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Finally! When I was just on the verge of giving up! :)

---

