---
title: "Monitor resolution defaults back to 1024"
date: 2009-06-17
forum: Multimedia Software
---

### Post by Icefyre on 2009-06-17
Hi everyone,

I'm brand new on linux, kicked out Windows completely and I managed to get everything up and running to my (humble) tastes in no less than ... hmmm ... 4 weeks... ;)

I can't find a solution however for the following:

Since I have a new monitor I would like to have my default screen resolution to 1920x1200. It's not a problem to set it through the Nvidia-settings, but after every logout or reboot it's switching back to 1024. 

The Xorg.conf file shows me: 

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "**1920x1200 +0+0**; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection

I've tried "sudo dpkg-reconfigure xserver-xorg", but there were no screen resolutions I could choose from.
I've tried to manually edit the xorg.conf file to no effect.
I've tried "**sudo nv[B]idia-xco**nfig" **and** "sudo nvidia-settings"[/B]

The strange thing is that under my wife's account everything is .. well... like it should.
I guess I could try to copy her conf-file, but I still would like to know the underlying problem. Is there maybe another process that "overlaps" the Nvidia-setting? Like compiz? or the emerald theme manager? 

Any help is greatly appreciated because I kinda stuck her!

thanx in front

---

### Post by xc3RnbFO8P on 2009-06-17
Try System> Preferences> Display (choose No) and change the resolution

---

### Post by Icefyre on 2009-06-17
Wow, thank you for the fast reply!

It seems to be solved now - I tried a log out and a reboot. 

The monitor settings showed 1920X1200 however. I changed the refresh rate from 50.1 to 50... could this somehow be the reason why the 1024 settings kept coming back?

thank you in any case

---

### Post by xc3RnbFO8P on 2009-06-17
> The monitor settings showed 1920X1200 however. I changed the refresh rate from 50.1 to 50... could this somehow be the reason why the 1024 settings kept coming back?
I don't know, could be , 50Hz is my only option. (I got 24" LG)

---

### Post by Icefyre on 2009-06-17
I have the same screen - LG 24" - pretty awesome to look at...

Thanks for the help

---

