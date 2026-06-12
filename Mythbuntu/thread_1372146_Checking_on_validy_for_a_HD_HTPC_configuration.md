---
title: "Checking on validy for a HD HTPC configuration"
date: 2010-01-04
forum: Mythbuntu
---

### Post by marclg on 2010-01-04
Hi,

1st happy New Year 2010 ):P

2nd I am planing to build a new machine. It is ^planned to be a Mythbuntu HD machine.

I look for the following features:
1. Playback 1 full HD stream + record 2 full HD streams
2. Picture in picture Bluray mode support
3. CAM support for decrypting for DVB-S2 and DVB-T HD
3. No gaming

I plan for the following configuration in a Zalman HD501 or Silverstone LC20 case:
```
1. Corsair TWIN2X4096-8500C5D Dominator 4GB 2 X 2GB DDR2 CL5
2. Gigabyte GA-EP45-EXTREME
3. Intel Core 2 Duo E8500 Dual-Core Processor, 3.16 GHz
4. Cooler Master Silent Pro M500
5. Hitachi 2 TB Deskstar SATA 7200 RPM 32 MB Cache
6. Noctua NH-U9B + 2 x Noctua NF-R8
7. Gigabyte GV-R485MC-1GI  (HD4850 - 1Go - passive)
8. 2 x FloppyDTV T/CI + 1 x FloppyDTV-S2
9. Whatever Bluray / DVD / CD combo burner

```

I wonder if this is an overkill and if I Mythbuntu will be able to support all my features.

thanks for your help.

Regards

Marc

---

### Post by larsolav on 2010-01-04
Happy New Year to you too!
Just one comment on the graphics card. Nvidia seem to be the gpu preferred for mythtv users. Nvidia has drivers so that HD playback is handled by the GPU using VDPAU. I don't think the Radeon cards have the same capabilities in linux....

---

### Post by marclg on 2010-01-05
Bonjour,

thanks for the information.

what about this one from NVidia: GV-N98TSL-1GI
Fanless, GeForce 9800 GT with 1 GB of DDR3

But it seems NVidia has poor support for audio mixing on the HDMI

My open question is:

Is this kind of video card an overkill for HD HTPC?

Thanks


Marc

---

### Post by cascade9 on 2010-01-05
IMO, a 9800 is overkill. 

I would check the G210, theres fanless models in that range (there is also a fanless GT240). They have VDPAU support which is a good thing for a mythTV boxxen- 

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

larsolav is corrent, ATIs version of VDPAU is windows only, so I'd avoid the ATI cards for mythTV untill they finally fix that. 

BTW, just to really pick apart what you have specified- 

2TB 7200 HDD? You wont need 7200, a 5400 drive would be more than enough. Personally, I like the Western digital green power drives, but there are others. 

4GB? Nice, but you could get away with 2GB easy enough. 

Core2Duo 8500? More Mhz than you will need, I'd think about lower model. Seems like the 8200s and 8300s are gone now, but 8400 is still around. The 7xxx series C2D will have no problems with your stated uses (even quite a bit slower bottom of the line AMD and Intel CPUs will work fine if you have a nVidia card that supports VDPAU) 

Use the money you save from getting a slower CPU, less RAM, etc on a really nice power supply. Seasonic makes some really nice, quiet PSUs.

---

### Post by nicoloks on 2010-01-05
Way overkill in my opinion. If this is to be a myth box, then I'd assume that it is going to be turned on close to 24/7? If this is the case I'd be looking at getting your power consumption as low as possible, as with a VDPAU enabled GPU there really is no need for loads of CPU power. To give you an idea I've just put together a Celeron 2.8Ghz based system with an Nvidia 8400GS video card which supports VDPAU, and the CPU is only around 15% usage during HD content playback.

---

