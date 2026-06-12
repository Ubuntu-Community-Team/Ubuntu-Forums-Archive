---
title: "Weird look at dapper in a satellite a60 (Radeon 7000)"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by cartz on 2006-09-15
Hi, i just insatalled dapper in a satellite a60, and try to use "ati" and "radeon" drivers for the Radeon 7000 IGP, but in some buttons appears an weird look, i took a screen shot:
[http://img146.imageshack.us/img146/7062/gnomeweirdbk4.png](http://img146.imageshack.us/img146/7062/gnomeweirdbk4.png)

Anyone knows why this is happening?

Thanks.

---

### Post by zeeone on 2006-10-24
Hi, I had the same problem with ATI Mobility Radeon 7000 IGP. Changing the "Device" section to the following seemed to fixed it:

```

Section "Device" 
        Identifier      "ATI Technologies, Inc. Radeon Mobility 7000 IGP" 
        Driver          "radeon" 
        BusID           "PCI:1:5:0" 
        Option          "AGPMode" "4" 
        Option          "AGPSize" "16" # default: 8 
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!! 
        Option          "SWcursor" "true" # MUST BE TRUE!!! 
        Option          "RingSize" "4" 
        Option          "BufferSize" "2" 
        Option          "EnablePageFlip" "true" 
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!! 
        Option          "RenderAccel" "true" 
        Option          "AccelMethod" "XAA" # or XAA, EXA 
        Option          "DDCMode" 
        Option          "SubPixelOrder" "NONE" 
        Option          "ColorTiling" "true" 
        Option          "DynamicClocks" "true" 
        Option          "bioshotkeys"   "True" 
        Option          "XAANoOffscreenPixmaps" "true" 
EndSection

```

Keep in mind that the proprietary ATI driver does NOT work for Radeon 7000 series.

---

