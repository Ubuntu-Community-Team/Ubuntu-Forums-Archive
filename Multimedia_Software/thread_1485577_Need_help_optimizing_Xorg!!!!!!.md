---
title: "Need help optimizing Xorg!!!!!!"
date: 2010-05-17
forum: Multimedia Software
---

### Post by Cyclops_ on 2010-05-17
[FONT=Sans Serif]I would really  appreciate it if someone could help me figure out how to optimize my  Xorg and/or video setup.
[/FONT]
[FONT=Sans Serif]
[/FONT]
[FONT=Sans Serif]Here is the  situation: I just barely bought two brand new nVidia GeForce 250 GTS's  to support 3 LCD Monitors. (One of them is VGA only, odd I know).  With  the hardware that I have, one would think that my system would be rocket  fast!  But, when I have htop or my System Activity window open, most of  the time, Xorg is hogging CPU!  (Why would it do that when it has some  sweet video card hardware to take advantage of???)[/FONT]


[FONT=Sans Serif]Sometimes, things get a little choppy, like moving windows, etc.[/FONT]


[FONT=Sans Serif]Obviously, since it's a three monitor setup, I'm not able to run  Compiz or any other special compisitor (I wish I could, but I have  seriously tried and failed miserably!)[/FONT]


[FONT=Sans Serif]So, anyway, at this  point, I just want to config the computer to take as much advantage of  the video cards as possible instead of using the CPU!!!!  Any help with  this would be sooooo appreciated!
[/FONT]
[FONT=Sans Serif]
[/FONT]
[FONT=Sans Serif]Here are the monitor  resolutions: 
[/FONT]
[FONT=Sans Serif]24" VGA - 1900x1200 
[/FONT]
24" DVI - 1900x1200 

23"(?) DVI - 1900x1080


OS:                 Kubuntu 10.04 64 bit
nVidia Driver:  195.36.15

UPDATE: I forgot to add that my CPU is a Core2Duo 3.00 GHz!


Xorg.conf (relevant stuff):
```

Section "ServerLayout"
    Identifier      "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1   "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf  "Screen1"
    Option         "Xinerama" "1"
EndSection

Section  "Monitor"
    Identifier     "Monitor0"
    VendorName      "Unknown"
    ModelName      "KTC W2408S"
    HorizSync       31.0  - 75.0
    VertRefresh     56.0 - 63.0
    Option         "DPMS"
EndSection

Section  "Monitor"
    Identifier     "Monitor1"
    VendorName      "Unknown"
    ModelName      "NTS MB24W"
    HorizSync       30.0 -  74.0
    VertRefresh     50.0 - 61.0
EndSection

Section  "Monitor"
    Identifier     "Monitor2"
    VendorName      "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync        30.0 - 75.0
    VertRefresh     56.0 - 61.0
EndSection

Section  "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce  GTS 250"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section  "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce  GTS 250"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section  "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce  GTS 250"
    BusID          "PCI:4:0:0"
EndSection

Section  "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option          "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder"  "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
     EndSubSection
EndSection

Section "Screen"
    Identifier      "Screen1"
    Device         "Device1"
    Monitor         "Monitor1"
    DefaultDepth    24
    Option         "TwinView"  "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
     EndSubSection
EndSection

Section "Screen"
    Identifier      "Screen2"
    Device         "Device2"
    Monitor         "Monitor2"
    DefaultDepth    24
    Option         "TwinView"  "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
     EndSubSection
EndSection


```
Let me know if there is anything  else I could provide.

---

### Post by Cyclops_ on 2010-05-17
bump?

---

### Post by Cyclops_ on 2010-05-19
bump 2

---

### Post by Cyclops_ on 2010-05-24
Any takers?

---

### Post by drreed on 2010-05-24
I think you should start from the beginning, and think about how you went about installing your drivers, and which ones you used. There is a wiki entry about clearing out old video related files when you change drivers. Make sure you have a clean install and note versions. You may have to use an older driver if the most current doesn't work. I can't be of much more help than that, but since nobody else has answered you . . .

---

### Post by Cyclops_ on 2010-05-27
Thank you, drreed.

Well, it was a clean install, and then I just installed the latest nVidia drivers from the repo.  Do you think I should go backward and try out previous drivers?

---

### Post by drreed on 2010-05-30
> **Cyclops_ said:**
> Thank you, drreed.

Well, it was a clean install, and then I just installed the latest nVidia drivers from the repo.  Do you think I should go backward and try out previous drivers?

Sorry, I posted that right before I tore down both machines for upgrades, and I've been so busy killing my own rats I didn't see your response. Well I hope it's working out for you. Are you still working on this? I've never done what your trying to do, I'm building an ATI system as we speak to do it, and from what I've gleaned, I may get lucky or I may have my work cut out for me, who knows? LOL

I guess you've made sure that the dvi vga combo is OK from the card? You know, like some cards you can run dual monitors dvi+vga, and others it's hdmi+vga, and several of them won't do dvi+hdmi.

In the last two days have you tried:

1 card with 2 monitors
1 card with 1 monitor each
2 cards with 1 monitor on one card and none on the other

I would also try google and look around outside of these forums, someone may have a blog entry about their tests/successes.

In general, I think multiple cards in Linux causes twice the problems, but several people have indicated that the drivers support it (ATI) I don't know about Nvidia, but I think its the same.

I think you are probably on the right track with the drivers, but I'd check one more thing too, and thats the bios on the card. Those are new cards, and I think you can update the bios on the video card too, although you rarely hear people talk about doing it. (I heard that reading customer reviews of cards at Newegg)

As for going back to an older driver goes, that's probably the last thing I'd try, but it's certainly a good idea. An update could have broken something.

Also, check other distro forums for talk about the proprietary drivers. There may be a few Fedora, Redhat, etc. users using those. Another place to look might be in math/science related forums because that setup is being used for number crunching via CUDA. There might not be many Linux users running dual video cards for gaming (SLI) but there are quite a few in various scientific areas using multiple GPU's, and a lot of them use Linux.

---

