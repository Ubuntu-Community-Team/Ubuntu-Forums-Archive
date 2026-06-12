---
title: "Forcing 1360x768 resolution"
date: 2008-05-06
forum: Mythbuntu
---

### Post by deviantintegral on 2008-05-06
Hi,

I'm using Ubuntu 8.04, working on converting from Freevo to Mythbuntu.

I'm trying to get my Sharp LCD TV connected with DVI->HDMI on a ATI 9800 Pro to default to 1360x768, the highest native resolution. It's defaulting to 1280x720. I think it's because of a problem with the EDID info reporting a screen size of 0x0mm for 1360x768. Here's the info from Xorg.0.log:

```
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SHP  Model: fe9  Serial#: 16843009
(II) RADEON(0): Year: 2006  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 82  vert.: 46
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.633 redY: 0.333   greenX: 0.205 greenY: 0.702
(II) RADEON(0): blueX: 0.150 blueY: 0.081   whiteX: 0.292 whiteY: 0.322
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 74.2 MHz   Image Size:  820 x 461 mm
(II) RADEON(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
(II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 85.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) RADEON(0): Monitor name: SHARP HDMI
(II) RADEON(0): Ranges: V min: 55  V max: 76 Hz, H min: 15  H max: 48 kHz, PixClock max 90 MHz
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff004d10e90f01010101
(II) RADEON(0):         0010010380522e782a1bbea25534b326
(II) RADEON(0):         144a52afce0001010101010101010101
(II) RADEON(0):         010101010101011d007251d01e206e28
(II) RADEON(0):         550034cd3100001e662150b051001b30
(II) RADEON(0):         4070360000000000001e000000fc0053
(II) RADEON(0):         484152502048444d490a2020000000fd
(II) RADEON(0):         00374c0f3009000a20202020202001f3
```

Once I log in, I can use xrandr -s 1360x768 and it works fine. So, my solution was to use the Modeline given to me from the above, and disable EDID:

```
Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline "1360x768"   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync
        Gamma   1.0
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Boardname       "ati"
        Busid           "PCI:1:0:0"
        Driver          "ati"
        Screen  0
        Option          "MergedFB"      "off"
        Option         "IgnoreEDID"    "true"
EndSection
```

But, the TV doesn't recognize this as a valid signal. Is there something I've missed? Or some option to force Xorg to use the highest listed resolution, regardless of if it thinks it's valid or not?


Thanks,
--Andrew

---

