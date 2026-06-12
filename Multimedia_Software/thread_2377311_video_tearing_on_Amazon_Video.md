---
title: "video tearing on Amazon Video"
date: 2017-11-11
forum: Multimedia Software
---

### Post by jfaberna on 2017-11-11
I have mythbuntu 16.04 running on a Core i5 3450S. Most video plays well, but when I try to play Amazon Instant Video using either Firefox or Chrome I get video tearing on high motion scenes. I don't get this when playing videos on mythtv, Kodi, etc.

I'm guessing the video/gfx drivers are okay because they are the latest and up to date.  They should be common to all video playing. I don't have this issue on either browser on older hardware with either Windows 10 or OS X 10.12.6

I'm not really sure on how to chase this one down since it's a visual quality issue.

Jim A

---

### Post by Autodave on 2017-11-12
What graphics card are you using? Did you install any driver for the card? If so, where did you get it from?

---

### Post by jfaberna on 2017-11-12
There is no GFX card as this has Intel Ivy Bridge GFX built into the processor.  Standard Ubuntu install. No extra drivers for GFX.

---

### Post by Yellow Pasque on 2017-11-12
The last time I checked, FF and Chrome gave up on hardware decoded video accel under Linux. Both browsers have plugins/extensions that allow you to view videos using a local video player. I'm not sure about specific recommendations since I don't use them.

---

### Post by jfaberna on 2017-11-13
> **Temüjin said:**
> The last time I checked, FF and Chrome gave up on hardware decoded video accel under Linux. Both browsers have plugins/extensions that allow you to view videos using a local video player. I'm not sure about specific recommendations since I don't use them.

I think you are correct.  Researched further and found this link on how to solve it by using a beta PPA for Chromium to solve the hardware acceleration being off.

[https://www.pcsuggest.com/chromium-hardware-accelerated-video-decoding-linux/](https://www.pcsuggest.com/chromium-hardware-accelerated-video-decoding-linux/)

I'll try experimenting with this and see.

---

