---
title: "Monitor Out of range Message"
date: 2007-12-28
forum: Multimedia &amp; Video
---

### Post by heathguy on 2007-12-28
I have purchased an X2Gen mw19u (19" widescreen lcd) monitor and now when I try to log in I immediately receive a "Out of Range" message on the screen.

I have tried running "sudo dpkg-reconfigure xserver-xorg" and editing the xorg.conf file. The only modes that I have gotten to work are 800x600 and 1024x768.

The monitor is capable of running at 1440x900. I have tested it in Vista (dualboot) and it runs fine at 1440x900@60Hz.

After editing the xorg.conf file and booting in at 1024x768, if I go to "Screen and Graphics" and try to select any other settings, the drop down boxes for screen size and refresh rate contain NO options.

This is running Ubuntu 7.10, and using a GeForce 6150SE video card.

---

### Post by taurus on 2007-12-28
Try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then reboot.

---

### Post by heathguy on 2007-12-28
Okay I just tried your command with the added "-phigh" switch and now I cannot even get to the ubuntu splash/login screen.

---

### Post by heathguy on 2008-01-03
I am still experiencing this issue... The maximum display resolution I can get on this monitor (in linux) is 1024x768. The monitor is a widescreen 19" that is capable of 1440x900.

Does anyone else have any suggestions? Possibly somethings to manually add to the xorg.conf file?

---

### Post by Rubruquis on 2008-01-03
I have a very similar problem. I have a 22" widescreen monitor and when I set my resolution to 1680x1050, I can only see a black screen, although I can hear the opening sound.
I'm trying to solve this problem for days now, I've edited Xorg.conf a 100 times, tried everything and still couldn't make it work.

---

### Post by unarmedninja on 2008-01-03
i had similar problems with my lcd. I fixed it by adding the horizontal and vertical sync rates for my lcd. you'll need to lookup your monitor specs for them.
> 
Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "BenQ"
    ModelName      "BenQ T903"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection



> Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1792 1344
        Depth       24
        Modes      "1280x1024@60" "1280x960@75" "1280x960@60" "1280x1024@75" "1152x864@75" "1024x768@60" "1024x768@70" "1024x768@75" "832x624@75" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

you also might want to try switching to the vga port on the lcd instead of dvi. good luck.

---

