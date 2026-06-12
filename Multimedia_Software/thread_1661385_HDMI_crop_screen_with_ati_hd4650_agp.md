---
title: "HDMI crop screen with ati hd4650 agp"
date: 2011-01-06
forum: Multimedia Software
---

### Post by diegofrafer on 2011-01-06
I have a Ubuntu 10.04 x86 version and I have installed ati hd4650 agp graphic card with xorg drivers for ati. The graphic card is connected at Sony LCD 46W2000 hd 1080.

The proprietary drivers don't have support from ati hd650 "agp" now, therefore I have to use xorg drivers.

The problem is that the image show in the monitor is cropped at the top and botton.

I tried with xrandr utility for testing different modelines but all tests were failed.
I installed a Windows in other partition and the image is ok. With the app PowerStrip I obtained the correct modeline but when I probe with xrand the result is bad, the image in the monitor is crop.

Is it a bug? Anyone know a solution?

I attach a log file from Xorg.0.log, a modeline generated with PowerStrip and get-edid information.

Thanks.

---

