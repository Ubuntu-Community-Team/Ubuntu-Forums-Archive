---
title: "Building a MythTV Box"
date: 2009-11-22
forum: Mythbuntu
---

### Post by luigidk on 2009-11-22
I'm doing research on building a new MythTV box for .22 and HD recordings.  Here is a list of the components (Starting from scratch here).  Never built a box from scratch though - so any recommendations/alterations/etc. would be greatly appreciated.
Note: I would use HDHOMERUN and an HD-PVR for my tuners.. but I may keep my PVR-150 for my remote and Digital - but it seems that .22 is still having issues with that card.  SO one of my first questions is - if I use the HDHOMERUN and HD-PVR - would I still need a PVR-150?  Can the HD-PVR effectively replace using the PVR-150 as my remote?

Anything missing or incompatibilities? 

Case: SILVERSTONE Black 8.0mm aluminum front panel, 0.8mm SECC body GRANDIA GD04B Micro ATX Media Center / HTPC Case

MOBO: GIGABYTE GA-MA785GM-US2H AM3/AM2+/AM2 AMD 785G HDMI Micro ATX AMD Motherboard

CPU: AMD Phenom II X4 940 Deneb 3.0GHz Socket AM2+ 125W Quad-Core Black Edition Processor

Memory: Crucial 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500)

Video: 	ASUS ENGT220/DI/1GD2(LP) GeForce GT 220 1GB 128-bit DDR2 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card

Hard Drive: Western Digital Caviar Black WD1001FALS 1TB 7200 RPM SATA 3.0Gb/s 3.5" Internal

BluRay/DVD: 	PLEXTOR Black BD Combo SATA Model PX-B320SA LightScribe Support

HeatSink: SILVERSTONE NT01-E 2 x 60mm fans (optional) CPU Cooler

PowerSupply: [B]Rosewill Stallion Series RD400-2-SB 400W ATX V2.2 Power Supply

I'm right around the $1000 mark including the HD-PVR.  Would be happy to shave some cost from this - but want to ensure I'm set for a long time.

---

### Post by korgman on 2009-11-22
If your main concern is HD recordings, then I don't think you need that much power.  Since you have an NVidia video card, much of the CPU might be able to be offloaded if your chipset supports VDPAU.  I'm not familiar with the GT 220.  I have IGP 8300 and my CPU is at about 5% when I watch HD, and I have a Athlon processor.  I built my Myth Box last year for around $550.

---

### Post by ZedThou on 2009-11-22
> **korgman said:**
> If your main concern is HD recordings, then I don't think you need that much power.  Since you have an NVidia video card, much of the CPU might be able to be offloaded if your chipset supports VDPAU.  I'm not familiar with the GT 220.  I have IGP 8300 and my CPU is at about 5% when I watch HD, and I have a Athlon processor.  I built my Myth Box last year for around $550.

I especially agree with this point, even an ION Atom platform can do dual FE/BE duty using vdpau so I'd look at getting a less power-hungry processor. Also, a BD-ROM drive isn't particularly useful if you're only running mythtv.

---

### Post by Cuppa-Chino on 2009-12-23
Furthermore to just support the ION point, if you are building this for htpc duty only. a dual core is more than enough (due to separate video card even a Sempron would do), with video memory on the card you do not need 4gb of ram either.

Bear in mind that with a CPU like that you will generate loads of unnecessary heat, meaning fan spinning etc.

for reference my system uses on board graphics (nvidia 8300), an amd x2 5050e, 2gb of ram (512mb for video - never ever ever run out of ram) and works fine

---

### Post by pootle1 on 2009-12-23
I agree, definitely overcooked on the CPU front, go for one of the new low energy athlon duals (45w), which are lots cheaper as well.

You might want to go for a GT200 DDR3 model - I find that mine (with DDR2) is marginal for the highest quality de-interlacing when dealing with heavily compressed video streams.

---

### Post by LowSky on 2009-12-23
Blue-ray is a waste, Linux, heck windows support is horrible. Thanks to DRM. Just get a DVD-RW.

You also don't need a phenom x4 either you don't need that much power, get the Phenom x2 550 or Athlon 2 x4 for $100. save yourself some money. Use the cash to buy a second hard drive (HD takes up a lot of space).

And that heatsink might not fit I wouldn't get an aftermarket heatsink unless the noise is unbearable.

---

### Post by mars76 on 2009-12-23
Hi,

  Any reason why you are planning to get GT220 ??

  VDPAU is supported in 8600 GT as well and you can have this graphics card for less than $50 and it works great with VDPAU.

  I am using HD-PVR and have 8600 GT and they are working fine. Are you planning to rip the Bluray content ?? If not there is no point in getting a Blu-ray player . Even if you want to extract the content why not get a Blu-Ray reader for around $50. 

 Get a Power Supply which is Energy-Efficient       80 PLUS Certified. (Antec Earthwatts series, Seasonic etc..


 take it easy.

---

### Post by dad311 on 2009-12-23
Your processor is over kill.  I'm using a similar Gigabyte board with 4 gig of memory and a X2 processor. 

The only issue I have is that HDMI audio is not detected on my add-on Nvidia card.  Not a big problem because the on board optical port works great. This also might be an issue with the Video card.

Your power supply is on the small side for server.  It might be fine now, but if you start adding disks it may not be.  I just installed the power supply listed below because my 400 watt became to small.  The PS was $30.00 after rebate from Newegg and is DEAD QUIET, ZERO NOISE!  Highly recommended.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817153052](http://www.newegg.com/Product/Product.aspx?Item=N82E16817153052)

Try to find a fan-less Nvidia card.  The less fans you have the less noise your box will make.  THIS IS VERY IMPORTANT. 

I didn't see a remote on your list.  Newegg has several remotes that will work with mythtv, I use the one pasted below.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003](http://www.newegg.com/Product/Product.aspx?Item=N82E16880121003)

A 1TB drive will fill-up fast I would buy a 2TB drive.

Good luck.

---

### Post by dad311 on 2009-12-23
> **LowSky said:**
> Blue-ray is a waste, Linux, heck windows support is horrible. Thanks to DRM. Just get a DVD-RW.

You also don't need a phenom x4 either you don't need that much power, get the Phenom x2 550 or Athlon 2 x4 for $100. save yourself some money. Use the cash to buy a second hard drive (HD takes up a lot of space).

And that heatsink might not fit I wouldn't get an aftermarket heatsink unless the noise is unbearable.

Ive ripped several of my BLU-RAY disks.  Most ripped with dumphd others ripped with anydvd.  Average rip sizes after converting to mp4 with handbrake is 1.5 - 4 gig.  Playback looks great.

---

### Post by williammanda on 2009-12-24
One other consideration would be Adobe flash. I use Hulu and the Ion cpu doesn't have the horse power for good playback. See the following article:

[http://www.linuxtech.net/features/best_linux_htpc_motherboards.html](http://www.linuxtech.net/features/best_linux_htpc_motherboards.html)

---

### Post by dad311 on 2009-12-24
> **williammanda said:**
> One other consideration would be Adobe flash. I use Hulu and the Ion cpu doesn't have the horse power for good playback. See the following article:

[http://www.linuxtech.net/features/best_linux_htpc_motherboards.html](http://www.linuxtech.net/features/best_linux_htpc_motherboards.html)

Im not sure any CPU has what it takes for Adobe Flash.  Flash is a PIG.

---

### Post by luigidk on 2009-12-27
Thanks for all the great tips - I continue to change the config based on all the advice.  Really like the help on the video card - that has been my biggest concern.  There is a new fanless GT220 just hitting the market - but if an 8600 will do the job - great!  THough I am concerned if I have issues with VDPAU that I have a big enough video card.  WIll take another look at the power supply.

WIll post my new config shortly!  

Thanks again!

---

### Post by luigidk on 2009-12-31
OK - I've modified my 'build' based on all the great input from this forum - as well as at Newegg eggxpert.
I'm still very torn on the video card as I want to be 100% sure that I can drive HD media if for some reason VDPAU doesn't work correctly.  At this time I'm waiting for the Zotac fanless GT220 card to become GA - but am very open to suggestions.  
[http://www.zotacusa.com/zone-geforce-gt-220-1gb-128-bit-ddr2-625mhz-800mhz-zt-20204-20l.html](http://www.zotacusa.com/zone-geforce-gt-220-1gb-128-bit-ddr2-625mhz-800mhz-zt-20204-20l.html)

LIAN LI Black Aluminum PC-C39 Micro ATX Media Center / HTPC Case - Retail
(expensive but want a very nice case with some room - will sit with my other A/V components)
ASUS M4A785TD-M EVO AM3 AMD 785G HDMI Micro ATX AMD Motherboard - Retail
(require Firewire and wanted AM3)
AMD Athlon II X2 250 Regor 3.0GHz Socket AM3 65W Dual-Core Processor Model ADX250OCGQBOX - Retail
(seems to be the lowest watt I can find)
G.SKILL 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory Model F2-8500CL5D-4GBPK - Retail
Antec EarthWatts Green EA-380D Green 380W Continuous power ATX12V v2.3 / EPS12V 80 PLUS BRONZE Certified Active PFC Power ... - Retail
(Sound and power is a concern - this should be plenty for this build)
2 - Western Digital Caviar Green WD10EADS 1TB SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive
(2 1-tb drives seems to be a better deal than a single 2tb)
PLEXTOR Black BD Combo SATA Model PX-B320SA LightScribe Support - OEM
(want to be able to play BluRay discs and still need a dvd drive)
Hauppauge HD PVR High Definition Personal Video Recorder 1212 USB 2.0 Interface - Retail
(will be using my HDHOMERUN and this for all my cable in)
AVS Gear GP-IR01BK Windows Vista Infrared MCE Black Remote Control
(will replace my PVR-150) with this - should be less problematic

---

### Post by myth_cougar on 2010-01-01
At this time I would suggest steering clear of the gt220.  I bought an XFX one expecting great things, but I have had nothing but problems with it.

It works ok with the nv driver, but is a little slow when playing some media.  Trying the nvidia drivers, I found it isn't supported by the 185 drivers in karmic, you need the 190 drivers at least.  I tried using the avenard repos, but that was problematic in itself, although I did eventually install the new drivers, but for some reason it has killed my sound which was working fine from the initial install and updates.  It was only after installing from avenard that the sound died and I have been struggling to get it working again as there doesn't seem to be any errors shown up anywhere and nothing apparent in the avenard packages that would suggest some conflict!

If anyone has any info on this I would appreciate it.

---

### Post by Chuffinora on 2010-01-01
I too was wanting the fanless 220.  But since I also wanted to upgrade my system this xmas, I did not wait.  I got the fanless 210

[www.newegg.com/Product/Product.aspx?Item=N82E16814127454&cm_re=nvidia_210-_-14-127-454-_-Product](www.newegg.com/Product/Product.aspx?Item=N82E16814127454&cm_re=nvidia_210-_-14-127-454-_-Product)

This runs VDPAU fine.  It cannot do the advanced 2X de-interlacing, only 1X  but the picture looks great to me from my HDPVR  1212  (When it is running - see my other thread about the HDPVR problems I am having,  but for HD from a cable box thats the only option)

---

