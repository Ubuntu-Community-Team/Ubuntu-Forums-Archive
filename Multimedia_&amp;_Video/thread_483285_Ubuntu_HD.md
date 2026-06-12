---
title: "Ubuntu HD?"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by spiker611 on 2007-06-24
Hello everyone.

I'm looking for some help with a problem.  First off, heres what i'm working with.

Basic computer with decent components
nVidia 7900GS (evga if that matters)
Ubuntu 7.04 with nvidia drivers from restricted manager
Sony XBR-960 (kd-34xbr960) 34 inch HDTV
DVI - HDMI cable (HDMI in TV)
Component TV out hooked into TV.

I have tried the DVI - HDMI connection many times and simply cannot get a reasonable picture.  I can get a resolution of 1280x720 with nvidia-settings, but the edges of the screen are not visible (extend beyond TV), and there is a ton of flicker.

I tried xvidtune - not supported by nvidia drivers.  I tried powerstrip in windoze, wouldn't let me change the screen size without going black.  Wont let me change refresh rate either.

I tried the component-out with no luck, even when enabling it in xorg.conf and setting it to HD resolutions.  Still, very overscanned.

Im willing to try anything software related to fix this problem - but unfortunately I cannot exchange hardware or buy new hardware.  Please, if anyone can help me out I would appreciate it VERY much.

---

### Post by Scunizi on 2007-06-24
First you might have to force the monitors native resolution in xorg.conf.  Some monitors use non-standard resolutions so the defaults in the computer are not correct.  Check the specs on that monitor then adjust xorg accordingly.  You're refresh rate should also be set to 60 in most cases.

---

### Post by spiker611 on 2007-06-24
As I forgot to mention, this is a CRT HDTV.  I have set the native resolutions of 1920x1080 and 1280x720 with tons of overscan.  Also, ubuntu seems to be running at 55 hz (vertical) refresh rate.

Strange?

---

### Post by baekster on 2007-06-25
CRT TVs are pretty notorious for their overscans.  Are you sure that the TV can support resolution above 1280x720?  From the product description I found on the web, it can display up to 720p (which is probably around 1280x720), so that probably explains why you can't get above that res.  Sony and samsung TVs (even LCDs) have fair amount of overscan with digital inputs (DVI, HDMI) from what I've researched online.  They compensate the overscan issue for having a separate VGA port that does not overscan...but that's analgue... (that's why I decided on Sharp LCD 1080p---no overscan at all!).

---

### Post by spiker611 on 2007-06-26
Yes, my CRT supports 1080i (television is displayed at this resolution..)

What i'm baffled about is that the digital HDMI port has overscan, but so does the 'analog' component cables at the same resolution!  (Using HDTV - OUT)

hmm..

---

### Post by dabl on 2007-06-26
I have the identical Nvidia card by EVGA, and I can testify that it provides a beautiful 1600 x 1200 display at 85 Hz refresh rate, on a Samsung SyncMaster 1100 CRT. So probably your issues are in the analog or HDMI domain, not the card itself.

---

### Post by baekster on 2007-06-26
> **dabl said:**
> I have the identical Nvidia card by EVGA, and I can testify that it provides a beautiful 1600 x 1200 display at 85 Hz refresh rate, on a Samsung SyncMaster 1100 CRT. So probably your issues are in the analog or HDMI domain, not the card itself.

Yea, I agree.  Since component isn't specifically designed for PC, it probably would have overscans (I think most TVs do that).  So it's the TV, not the card.

---

