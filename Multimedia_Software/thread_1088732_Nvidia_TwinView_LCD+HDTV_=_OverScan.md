---
title: "Nvidia TwinView LCD+HDTV = OverScan"
date: 2009-03-06
forum: Multimedia Software
---

### Post by PokeParadox on 2009-03-06
SOLVED

I was adding the modeline together wrong from the XP settings.

OK I'm almost ready to ditch XP completely the only thing standing in my way is being able to use my HDTV as a second monitor for my laptop.
The problem is same as many other people -Overscan. Now I have searched through the forums and found articles which help when using only a HDTV but not much when trying to correct the overscan while using TwinView.

My current status in this is I have a garbled screen on my laptop (supposed to be 1280x800) and a 480p resolution on my HDTV(supposed to 1280x720p). The TV is connected via HDMI

I'm almost at the end of my tether with this, so any help would be greatly appreciated. 

Here are my settings in XP
[IMG]http://img150.imageshack.us/img150/6061/kevsxpmodesettings.png[/IMG]

Here is some info on my two screens:
Laptop Display
```
(--) NVIDIA(0): Connected display device(s) on GeForce 8600M GS at PCI:1:0:0:
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0):     OEM 32'' TFT-TV (DFP-1)
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 330.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Native FlatPanel Scaling is
(--) NVIDIA(0):     not supported
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): DFP modes are not limited
(--) NVIDIA(0):     to 60 Hz refresh rate
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): DFP is internal to
(--) NVIDIA(0):     notebook
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for Nvidia Default Flat Panel (DFP-0) ---
(--) NVIDIA(0): EDID Version                 : 1.3
(--) NVIDIA(0): Manufacturer                 : NVD
(--) NVIDIA(0): Monitor Name                 : Nvidia Default Flat Panel
(--) NVIDIA(0): Product ID                   : 768
(--) NVIDIA(0): 32-bit Serial Number         : 0
(--) NVIDIA(0): Serial Number String         : 
(--) NVIDIA(0): Manufacture Date             : 2002, week 45
(--) NVIDIA(0): DPMS Capabilities            : Standby Suspend Active Off
(--) NVIDIA(0): Prefer first detailed timing : Yes
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 320mm x 200mm
(--) NVIDIA(0): Valid HSync Range            : 29.0 kHz - 50.0 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 0 Hz - 61 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 80.0 MHz
(--) NVIDIA(0): 
(--) NVIDIA(0): Detailed Timings:
(--) NVIDIA(0):   1280 x 800  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 70.95 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1328
(--) NVIDIA(0):     HSyncEnd, HTotal : 1360, 1440
(--) NVIDIA(0):     VRes, VSyncStart : 800, 803
(--) NVIDIA(0):     VSyncEnd, VTotal : 809, 822
(--) NVIDIA(0):     H/V Polarity     : -/-

```

32" Matsui HDTV
```
(--) NVIDIA(0): OEM 32'' TFT-TV (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): OEM 32'' TFT-TV (DFP-1): Internal Single Link TMDS
(--) NVIDIA(0): OEM 32'' TFT-TV (DFP-1): Native FlatPanel Scaling is
(--) NVIDIA(0):     supported
(--) NVIDIA(0): OEM 32'' TFT-TV (DFP-1): DFP modes are not limited to 60 Hz
(--) NVIDIA(0):     refresh rate
(--) NVIDIA(0): OEM 32'' TFT-TV (DFP-1): DFP is not internal to notebook
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for OEM 32'' TFT-TV (DFP-1) ---
(--) NVIDIA(0): EDID Version                 : 1.3
(--) NVIDIA(0): Manufacturer                 : OEM
(--) NVIDIA(0): Monitor Name                 : OEM 32'' TFT-TV
(--) NVIDIA(0): Product ID                   : 0
(--) NVIDIA(0): 32-bit Serial Number         : 0
(--) NVIDIA(0): Serial Number String         : 
(--) NVIDIA(0): Manufacture Date             : 2007, week 4
(--) NVIDIA(0): DPMS Capabilities            :
(--) NVIDIA(0): Prefer first detailed timing : Yes
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 160mm x 90mm
(--) NVIDIA(0): Valid HSync Range            : 15.0 kHz - 46.0 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 49 Hz - 61 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 80.0 MHz

```

and my xorg conf is attached. This is for the standard TwinView configuration which works, but the TV is horribly overscanned.

Again any help at all appreciated!

---

### Post by PokeParadox on 2009-03-06
I'm not normally one to bump topics, but I really need help with this.

---

### Post by PokeParadox on 2009-03-07
Well I messed up my Nvidia driver somehow and it looks like I need to do a fresh install.

Once I get to working status again, I'll still need help with my xorg...

---

