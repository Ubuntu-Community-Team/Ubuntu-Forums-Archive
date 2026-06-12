---
title: "Dual display (copy) on older LCD Projector"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by surahyo on 2007-08-27
Dear all,

I am a lecturer at University and currently using Kubuntu 7.04. I added some configuration on my xorg.conf in order to get dual display on my notebook and LCD projector. Here some lines were added:

Section "Device"
  identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
  boardname "Intel 945"
  busid "PCI:0:2:0"
  driver "i810"
  screen 0
  vendorname "Intel"
  Option "MonitorLayout" "NONE,LFP+CRT"
  Option "DevicePresence" "true"
  Option "CheckLid" "false"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Generic"
  modelname "1024x768 @ 60 Hz"
  HorizSync 31.5-48.5
  VertRefresh 50-70
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1024 768
    modes "1024x768@60"  "800x600@60" "800x600@56" "640x480@60"
  EndSubSection
EndSection

For some new LCD Projectors it works well, but for older ones I got message "unsupported signal" or something like that. Or sometime it shows but flickering.
It seems that the projector doesn't catch-up the frequency. I also got a message said that
"Please adjust to 1024x768 49Hz". Currently I use "1024x768 60Hz".
How can I add 49 Hz on xorg.conf?

Thank you
Surahyo

---

