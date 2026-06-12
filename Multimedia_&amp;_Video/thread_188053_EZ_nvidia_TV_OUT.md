---
title: "EZ nvidia TV OUT"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by October on 2006-06-03
GeForce4 Ti4600 and SVIDEO out.

NOTE: Depending on your specific hardware you m```

```ay not be able to run a higher resolution than 800x600.  The following information only works on my hardware IF I run both the desktop resolution and tv resolution no higher than 800x600.

1.) Make sure you have the latest nvidia drivers installed.

2.) Change "Device" section to look similar to the following (the important bits are the "Option" lines):

```
Section "Device"
  identifier "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nvidia"
  Option "TwinView" "Yes"
  Option "SecondMonitorHorizSync" "30-50"
  Option "SecondMonitorVertRefresh" "60"
  Option "TwinViewOrientation" "Clone"
  Option "TVOutFormat" "S-VIDEO"
  Option "TVStandard" "NTSC-M"
  Option "MetaModes" "800x600, 800x600"
  screen 0
EndSection
```

I also removed all the extra sections AFTER the "DRI" section so this is the last section in my xorg.conf:

```

Section "DRI"
  Mode 0666
EndSection

```

---

