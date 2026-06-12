---
title: "Configuring Sony Bravia KLV-32S400A Mythbuntu 8.10"
date: 2009-02-02
forum: Multimedia Software
---

### Post by MythNZ on 2009-02-02
Hi there,

My issue is as follows:

First off, I'm running an ASUS M3A78-EM motherboard with an ATI Radeon 3200HD integrated graphics card. This has an HDMI port that won't work yet but thats issue 2.

The main issue is when I run the Proprietry ATI FGLRX drivers the desktop runs ok but when I run the Myth front end it goes nuts. My investigations so far lead me to adding a modeline entry etc to the xorg.conf file. I've tried the closest settings in the following database with no luck.

[http://www.mythtv.org/wiki/Modeline_Database#Sony_Bravia_KLV-S32A10E_.28KLV-S40A10E.2C_KLV-S32A10E.2C_KLV-S26A10E.2C_KLV-S23A10E.2C_KLV-S19A10E.29](http://www.mythtv.org/wiki/Modeline_Database#Sony_Bravia_KLV-S32A10E_.28KLV-S40A10E.2C_KLV-S32A10E.2C_KLV-S26A10E.2C_KLV-S23A10E.2C_KLV-S19A10E.29)

I've tried using Google to find the refresh rate etc and attempted to find the TV manual. No luck on either counts though I'm sure the manual will turn up. I'll like to add that I realise that a refresh rate for an LCD TV is a redundant concept but assume that I need to still add this to the settings.

Currently my file looks like this:

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "fglrx"
EndSection


I'm fairly new at this so any help would be greatly appreciated. Thanks in advance.

---

### Post by MythNZ on 2009-02-04
Update:

When my TV first picks up a signal it displays 1360x760 60HZ so the answer was under my nose. I've tried the settings I found here which appeared to work for my tv.

[http://egopoly.com/2006/01/17/mythtv-setup-for-sony-bravia/](http://egopoly.com/2006/01/17/mythtv-setup-for-sony-bravia/)

Note the possible 1366 typo - it should be 1360

I say this possibly worked but after further investigation I think my issue is more like this one:

[http://ubuntuforums.org/showthread.php?t=1007090](http://ubuntuforums.org/showthread.php?t=1007090)

I've tried the suggested fix with no joy so I'm thinking its time to try another driver. Yet more learning to be done. I've also read that a lot of people with an on board Radeon 3200HD usually buy a nVidia card as the 3200HD is problematic with Myth. Lets hope it doesn't come to that.

---

