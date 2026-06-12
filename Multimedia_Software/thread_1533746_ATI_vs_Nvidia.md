---
title: "ATI vs Nvidia"
date: 2010-07-18
forum: Multimedia Software
---

### Post by itlarson on 2010-07-18
Are there big disadvantages to building a computer around a motherboard with ATI Radeon graphics instead of Nvidia?  I am using an AMD CPU to save money, but all the motherboards AMD recommends use ATI.  I have always used Nvidia in the past, And am not sure what the current state of ATI Linux drivers is.  I know I would be giving up VDPAU acceleration for video playback, but hopefully the Athlon™ II X4 635 processor I am looking at has enough horsepower to handle this on it's own, even for high-def h264.

---

### Post by JDorfler on 2010-07-18
I'm running all AMD and I have no problems.  I have used nVidia, and again, no problems.  There's no real world advantage to either.

---

### Post by cascade9 on 2010-07-18
Apart from no VDPAU, and slight differences in power consumption/game performance, the main difference is the ATI driver support just isnt as good as nVidia. 

There is XvBA (hardware video decoding) for ATI, but as far as I know its still a work in progress and a long way from as mature as VDPAU. 

A Athlon II X4 635 should have enough power to play HD video, but its going to use a lot more CPU power than an nVidia card + VDPAU. 

> **itlarson said:**
> I am using an AMD CPU to save money, but all the motherboards AMD recommends use ATI.

Do you have a link to AMDs recommended motherboards? Just out of intrest. 

BTW, Not all of the ATI chipsets have onboard video. Some of the models with onboard video are cheaper than a motherboard + video card, but some of them are actually more expensive. 

What model motherboard were you thinking of getting?

---

### Post by gradinaruvasile on 2010-07-18
Get a AMD with nvidia onboard mobo if you dont play demanding games. You can add a PCI express add-on card if needed anyway (preferably nvidia because of the driver support).

I have a ASUS M3N78-VM (socket AM2/3) that has a nvidia 8200 onboard (dual monitors+HDMI output) and it works great. It was inexpensive relatively to its performance (also the on board cards use less power).
If you want to to play HD movies without VDPAU make sure you use mplayer-mt otherwise you end up using only 1 core and even a core2duo skips frames on 1080p.
This onboard card  does VDPAU with 1080p on a Athlon 3200+ single-core CPU @ 10-15% CPU.
The quake3 based games run on it without problems (TCE, Enemy Territory, Urban Terror, Smokin Guns etc).
I play CounterStrike 1.6, Oblivion and Medieval 2 on it via Wine (not that fast in these last 2 games partly because i enabled HDR, but playable on my ancient Athlon 3200+).

It is also extremely stable, i never had X crash on it. I use Debian Squeeze on it (with the drivers from nvidia's site), but it worked before in Ubuntu 9.10 aswell.
I would recommend the ASUS M4N series as they support out of the box the AM3 chips without any BIOS upgrade.

---

### Post by itlarson on 2010-07-18
Here's the list of motherboards for the procesor I was refering to:

[http://products.amd.com/en-us/RecommendedMBResult.aspx?f1=AMD+Athlon%E2%84%A2+II+X4&f2=635&f3=C2&f4=&f5=&f6=&f7=&f8=95+W]("http://products.amd.com/en-us/RecommendedMBResult.aspx?f1=AMD+Athlon%E2%84%A2+II+X4&f2=635&f3=C2&f4=&f5=&f6=&f7=&f8=95+W")

This is a compleat list of amd procesors which can be used to get detailed specs, including the recomended motherboard list:

[http://products.amd.com/en-us/DesktopCPUResult.aspx]("http://products.amd.com/en-us/DesktopCPUResult.aspx")

It sounds like my options are live with less graphics performance, live with the extra expense and power consumption of a separate video card, or use a non-recommended motherboard.  I suppose I could go with Intel instead, but comparable Intel processors cost almost twice as much. 

What are peoples opinions on these options?

---

### Post by cascade9 on 2010-07-18
> **itlarson said:**
> Here's the list of motherboards for the procesor I was refering to:

[http://products.amd.com/en-us/RecommendedMBResult.aspx?f1=AMD+Athlon%E2%84%A2+II+X4&f2=635&f3=C2&f4=&f5=&f6=&f7=&f8=95+W](http://products.amd.com/en-us/RecommendedMBResult.aspx?f1=AMD+Athlon%E2%84%A2+II+X4&f2=635&f3=C2&f4=&f5=&f6=&f7=&f8=95+W)

This is a compleat list of amd procesors which can be used to get detailed specs, including the recomended motherboard list:

[http://products.amd.com/en-us/DesktopCPUResult.aspx](http://products.amd.com/en-us/DesktopCPUResult.aspx)

It sounds like my options are live with less graphics performance, live with the extra expense and power consumption of a separate video card, or use a non-recommended motherboard. I suppose I could go with Intel instead, but comparable Intel processors cost almost twice as much. 

What are peoples opinions on these options?

Ohh, that list. For some reason I thought that got taken down years ago, guess I was wrong :) 

I'd take that list with a grain of salt...several grains would be more realistic, and a whole bucket wouldnt be too far from the truth. 

As long as you dont go crazy and get a 'gamers' video card (GTS250, GTX2XX, GTX4XX) video cards dont eat a huge amount of power. A GT220, which is more than fine for HD, is using only about 8watts at idle and 22watts peak

[http://www.xbitlabs.com/articles/video/display/gf-210-gt220_5.html#sect0](http://www.xbitlabs.com/articles/video/display/gf-210-gt220_5.html#sect0)

Dont forget, that your CPU will eat about 3-4 times as much power at full load, and VDPAU + a video card will use less power than CPU decoding. If you play a fair amount of videos on your computer total power use could well be lower (if you used it for nothing but video, or video + multitasking, it sure would).

> **gradinaruvasile said:**
> I would recommend the ASUS M4N series as they support out of the box the AM3 chips without any BIOS upgrade.

Just being a fact-nazi, and pointing out that you need the M4N78 XXX series (NOT the M4N78, it has no video). There are M4N motherboards that have the old 7025/nForce 630 and (bad! Yuck!..OK, not really 'yuck' but useless for VDPAU) and the 7XXa/9XXa chipsets. 

Id rather have a AM3 chipset with DDR3 and no video, with a standalone video card myself, but I know I'm biased.

---

### Post by raymondvillain on 2010-07-18
I agree with Cascade9.  I have a motherboard with Radeon HD3200 and I've had lots of headaches with the video setup.  ATI does make drivers for Linux but it took me days and days to figure out how to set things up.

One thing I've learned is that if one updates Ubuntu, from, say, 9.10 to 10.04, the video is trashed because the latest ATI driver is not part of the distribution.

One has to go the ATI driver website, download and install the new driver so that video will function in the updated Ubuntu.  Atleast that was true for my setup.

I also have a notebook PC with Nvidia graphics and there is never any trouble updating Ubuntu.

---

### Post by itlarson on 2010-07-19
There are only two motherboards under $100 on Newegg which have both am3 and Geforce 8200. One is by MSI, and the cheaper one is by Asrock.  I am leaning towards the MSI board due to it having more reviews and my being more familiar with the brand.

---

