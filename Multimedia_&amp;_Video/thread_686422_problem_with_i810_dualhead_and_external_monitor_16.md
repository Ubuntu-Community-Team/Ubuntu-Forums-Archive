---
title: "problem with i810 dualhead and external monitor 1680x1050@60"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by fguillen on 2008-02-03
Hi people.

I am losting a lot of time trying to configure a external monitor "Samsung SyncMaster 206BW".

I am using ```
 Ubuntu 7.10.
```

and

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

I have followed a lot of forums an google stuff.

At the end I have obtained to have a 1680x1050 resolution but the image is not centered on screen and is not possible to center it by the menu of the monitor, the image is not good also.

the monitor sais to me that "The optimal resolution is 1680x1050 and 60Hz".. I was looking on the Xorg log and found this:

```
(II) I810(1): Attempting to use 56.00Hz refresh for mode "1680x1050" (85a)
```

Is possible that the refresh rate makes the error of the not centered image?

Here is the 915resolution -l:

```
$ sudo 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.3

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 800x600, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1680x1050, 24 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 800x600, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1680x1050, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 800x600, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1680x1050, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 60 : 1280x800, 8 bits/pixel
Mode 61 : 1280x800, 16 bits/pixel
Mode 62 : 1280x800, 32 bits/pixel
```

I hacked it for obtain the 1680x1050 resolution.

I attach the Xorg.0.log and the xorg.conf.

Thanks for the help
f.

---

