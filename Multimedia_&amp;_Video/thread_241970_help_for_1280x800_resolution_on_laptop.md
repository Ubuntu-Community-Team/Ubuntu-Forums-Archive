---
title: "help for 1280x800 resolution on laptop"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by bvidinli on 2006-08-23
hi,
i tried many thing for working on 1280x800 resolution, but did not succeed up to now... 
my laptop supports 1280x800, it works on win2000 as 1280x800

i tried dpkg-reconfigure xserver-xorg
i tried 915resolution and set one of bios settings as 1280x800

i added horizsync and vertrefresh to my xorg.conf
my xorg.conf contains only modeline for 1280x800, 

but still does not work...


please help...

---

### Post by bvidinli on 2006-08-23
my Xorg.0.log contains:
 
 *(WW) (1280x800,Generic Monitor) mode clock 83.462MHz exceeds DDC maximum 80MHz
 
 this may be the problem but i didnot solve yet,
 
 my xorg.conf contains following:
 
 Section "Monitor"
         Identifier      "Generic Monitor"
         Option          "DPMS"
         HorizSync       48-50
         VertRefresh     59-61
         ModeLine "1280x800" 68.56 1280 1336 1472 1664 800 801 804 824 -HSync +VSync
 EndSection
 
 Section "Screen"
         Identifier      "Default Screen"
         Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
         Monitor         "Generic Monitor"
         DefaultDepth    16
         SubSection "Display"
                 Depth           16
                 Modes           "1280x800"
         EndSubSection
         SubSection "Display"
                 Depth           24
                 Modes           "1280x800"
         EndSubSection
 EndSection
 
 
 
 
 915resolution output :
 
 # 915resolution -l
 Intel 800/900 Series VBIOS Hack : version 0.5.2
 
 Chipset: 915GM
 BIOS: TYPE 1
 Mode Table Offset: $C0000 + $269
 Mode Table Entries: 36
 
 Mode 30 : 640x480, 8 bits/pixel
 Mode 32 : 800x600, 8 bits/pixel
 Mode 34 : 1024x768, 8 bits/pixel
 Mode 38 : 1280x1024, 8 bits/pixel
 Mode 3a : 1600x1200, 8 bits/pixel
 Mode 3c : 1280x800, 16 bits/pixel
 Mode 41 : 640x480, 16 bits/pixel
 Mode 43 : 800x600, 16 bits/pixel
 Mode 45 : 1024x768, 16 bits/pixel
 Mode 49 : 1280x1024, 16 bits/pixel
 Mode 4b : 1600x1200, 16 bits/pixel
 Mode 4d : 1280x800, 16 bits/pixel
 Mode 50 : 640x480, 32 bits/pixel
 Mode 52 : 800x600, 32 bits/pixel
 Mode 54 : 1024x768, 32 bits/pixel
 Mode 58 : 1280x1024, 32 bits/pixel
 Mode 5a : 1600x1200, 32 bits/pixel
 Mode 5c : 1280x800, 32 bits/pixel
 
 
 any help is welcome

---

### Post by simohell on 2006-09-06
> **bvidinli said:**
> hi,
i tried 915resolution and set one of bios settings as 1280x800


You might need to set several bios settings to 1280x800 - all the smaller ones. It worked for me. (for me it is however x768... but that's just a different panel)

I made a short script (/etc/init.d/915res.sh) :

```
# !/bin/sh

915resolution 30 1280 768
915resolution 32 1280 768
915resolution 34 1280 768

```

and set it run each time I boot:

```
/etc/init.d$ sudo update-rc.d 915res.sh start 20 S .
```

So far it does prevent me from using hibernation, because I don't yet know how to run it to get it working before X reappears. Thus X gives me black screen although everything else works. Sleep works fine...

---

### Post by simohell on 2006-09-06
If this works, and there is the hibernation issue, make a copy of the same script to /etc/acpi/resume.d -folder. Check that it has the same access rights as the other scripts in the same directory.

Maybe start the name with "14-". Also one might want to rename/rewrite one of the "13-855-resolution-set.sh" just replacing 855 everywhere with 915.

---

