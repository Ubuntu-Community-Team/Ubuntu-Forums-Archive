---
title: "Problems setting up mulitple monitors with 2 x HD 7770"
date: 2013-09-14
forum: Multimedia Software
---

### Post by stretch2 on 2013-09-14
Hello, I'm new to Linux, and this is my first post, please be gentle :D

I have 2 x HD 7770 video cards (Crossfire not enabled)

```
lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde XT [Radeon HD 7770 GHz Edition]
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde XT [Radeon HD 7770 GHz Edition]

```

I have downloaded and installed the drivers from AMD, which detects and enables one of the cards. So, to get the other one working, I edited xorg.conf to the following:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen      1  "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection


Section "Module"
EndSection


Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection



Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
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

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    Monitor    "aticonfig-Monitor[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection




```

This gets me to the point where the main screen is as normal, and the second screen is just grey (no unity bar or anything). So what I want is to either:
1. Have the screens duplicate
or
2. Have the screen extend, and able to drag stuff across

When I enable Xinerama in Catalyst Control Center (Allowing you to drag from screen to screen), and restart, when I log in, it just goes to black screens and bugs out ... In hindsight, I should have checked what those errors said ...

So, basically, I'm wondering if anyone else has encountered this problem, or if they know of a different way to control screen cloning/extension, or if they know the location of the logs for the errors ...

Many thanks, Chris  [IMG]http://ubuntuforums.org/images/icons/icon10.png[/IMG]

---

### Post by stretch2 on 2013-09-14
Just a little update on this, I enabled CrossFire, and then after restart, I logged in and nothing would load, the screen just stayed black ... xorg.conf was not changed ... Thinking that the CrossFire option would be stored on the ATI cards themselves (Need to research that, see if I'm right), I tried installing CCC on my Windows OS, but was only given limited options ... So, thinking that my only option was to re-install Ubuntu, I first tried removing the CrossFire cable on the cards, and to my surprise, it worked :D ... Yeah ... I'm a kinda fault finding god ... Lol ... 

But my first problem is still there ... And I've now found a new one, that I can't enable CrossFire Lol

---

### Post by QIII on 2013-09-14
Hello!

I've never used Crossfire because I've always used multiple cards for GPGPU, so I'm not sure how to advise on that.

You may be having difficulty if only one GPU is initialized.  The installer should have detected all of your cards, but you might want to try making sure they are both initialized by 

```
sudo amdconfig --adapter=all --initial
```

and rebooting.

Best wishes.

---

### Post by stretch2 on 2013-09-14
Hi, thanks for the help, but it doesn't seem to have done anything :/

I ran the command you said, and then shutdown and replaced the crossfire cable (With the PSU turned off also)

After rebooting, it allowed me to log in as normal, but now in CCC it doesn't give me the option to enable crossfire Lol ... 

Tomorrow I may try again to extend my displays, after doing the command you supplied, and I will post the results here :D

Im getting there slowly by the looks of it Lol ...

---

