---
title: "xorg.conf always gets overwritten"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by darkphader on 2008-04-21
Running Hardy Heron with all of the latest updates. Have a very fine working xorg.conf that Kubuntu now decides (it didn't always do this) to overwrite with a totally non-working one. The new generated xorg.conf hoses a working xorg.conf and only allows for a lousy 640x480 on a 21" Samsung 213T.

From working xorg.conf:```
Section "Monitor"
        Identifier      "Samsung 213T"
        HorizSync       30-93
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Samsung 213T"
        Device          "Configured Video Device"
EndSection

``` From non-working generated xorg.conf:```
Section "Monitor"
        Identifier      "Samsung 213T"
        Modelname       "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Samsung 213T"
        Device          "Configured Video Device"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1920    1440
                Modes           "1600x1200@60"  "1600x1200@75"  "1600x1200@65"  "1600x1200@70"  "1400x1050@75"  "1792x1344@60"  "1400x1050@60"  "1856x1392@60"  "1280x960@75"   "1920x1440@60"  "1280x1024@60"  "1280x960@60"   "1280x1024@75"  "1152x864@75"   "1024x768@60"   "1024x768@70"   "1024x768@75"   "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    "640x480@60"
        EndSubSection
EndSection

```And what's that stupid virtual window of 1920x1440?

The first one works, the second one doesn't. From the log:```
*(II) I810(0): Not using mode "1600x1200@65" (hsync out of range)
(II) I810(0): Not using mode "1600x1200@60" (hsync out of range)
(II) I810(0): Not using mode "1600x1200@75" (hsync out of range)
(II) I810(0): Not using mode "1600x1200@70" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)
(II) I810(0): Not using mode "1600x1200" (hsync out of range)

```Everything would be fine if the system did not continually overwrite xorg.conf. How to resolve this issue? Thanks.

Chris

---

### Post by webaake on 2008-04-23
Same here! I do get some changes if manually editing the xorg.conf file and choosing a different resolution. But after restart same ol' 640x480!!

I've tried with Envyng and the latest driver from there, and right now I have Nvidia driver 173.x beta working, sort of.

---

### Post by mjezell on 2008-04-23
Hi,

Same problem for me.  Is there anyone that can explain this?

---

### Post by everweb on 2008-06-12
In my case the offender was livna-config-display

$ sudo livna-config-display

uncheck the checkbox that says "Allow livna-config-display to edit configuration files" and control will be restored...

---

### Post by everweb on 2008-06-12
I also found that after switching off the livna-config-display, my DPI was pushed to 115x115 by EDID (this came from reading the logs under /var/log/Xorg.0.log).
The resolution really was 1680 by 1050 but everything was huge !

The following describes what I did to fix it: [http://gentoo-wiki.com/HOWTO_Set_DPI_(Dots_Per_Inch)]("http://gentoo-wiki.com/HOWTO_Set_DPI_(Dots_Per_Inch)")

In summary, add the DisplaySize setting to the Section "Monitor" of your xorg.conf according to what you want your DPI to be (I chose 96x96), then add Option "UseEdidDpi" "false" to Section "Screen" (or Section "Device", it apparently doesn't matter)

---

