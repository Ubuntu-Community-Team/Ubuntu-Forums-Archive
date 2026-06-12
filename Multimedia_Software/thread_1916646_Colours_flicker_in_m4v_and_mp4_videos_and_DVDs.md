---
title: "Colours flicker in m4v and mp4 videos and DVDs"
date: 2012-01-28
forum: Multimedia Software
---

### Post by OiseauVernal on 2012-01-28
The screenshot below shows what videos look like when I try to play m4v and mp4 videos and DVDs in both Totem and VLC. I'm running Lucid on a laptop with the following:

Processor: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57
Video card: RS690M [Radeon X1200 Series]
RAM: 2GB DDR2

If you need any more info, just ask. And thanks in advance for any help you can give.

---

### Post by WasMeHere on 2012-01-28
Hi MrBird,

It has been difficult for many people to run ATI Radeon graphics with Ubuntu. The standard driver does not work well, and there are often (but not always) problems with the proprietary drivers. Let us hope someone who knows more about ATI will show up in your thread :-)

You are running ***Lucid***, which I often recommend for computers that are not brand new.

I think your computer should be powerful enough to run graphics for video clips of DVD quality (if not 1920x1080-50p high definition video). Once I had such artifacts on a video, it actually was because the video was badly coded, so it could be different reasons.

Finally, it might be worthwile trying a new version of ***Lubuntu***, which has an ultra-lightweight desktop environment and it has newer video drivers included in the kernel.

Have fun finding out :-)
Olle

---

### Post by OiseauVernal on 2012-01-30
Finally fixed it by installing Xine, but thanks for the reply Mr Wiklund :)

---

### Post by bcarlowise on 2012-01-31
I believe those video formats require third party codecs such as the ones contained in the gstreamer plugins packages.

---

