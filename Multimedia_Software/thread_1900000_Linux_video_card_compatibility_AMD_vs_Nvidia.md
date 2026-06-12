---
title: "Linux video card compatibility: AMD vs Nvidia"
date: 2011-12-25
forum: Multimedia Software
---

### Post by BLaZuRE on 2011-12-25
I am currently looking to purchase a video card for a system I am building for myself.  I have dealt with integrated Intel in the past.  I am now wondering which one would be better for me: AMD or Nvidia?  There are several items I'm trying to consider:

**Efficiency** - sure the cards do fine in Windows, but how efficient are the drivers for Linux?  For casual word processing?  Video processing/production?
[B]
Drivers[/B] - will there be support for the cards out of the box?  Proprietary or open source?
[B]
Future-proof[/B] - Is there any risk of losing driver support in the future?
[B]
Issues[/B] - I don't want to have issues and have crashing drivers or the like.  Is this common?

**Linux-wide support** - How is driver support for other flavors like Debian or Gentoo?

I've already been browsing the web a bit but I'm still conflicted and don't know which to get.  I have a budget of roughly around $100-$150 for a card.  I'll either get in the next couple days or in a few weeks (hopefully prices drop in January).  Also, I'll probably bypass Lucid Virtu (I don't know if there's a Linux alternative) and go directly to discreet graphics since I have a **23" dual-screen 1920x1080 via DVI** inputs.

Thank you in advance!

---

### Post by Pistolebob on 2011-12-25
Nvidia has good proprietary drivers, AMD has bad proprietary drivers that may or may not work well with your videocard.

---

### Post by inobe on 2011-12-25
nvidia

the day they start to suck is the day they stop selling hardware.

---

### Post by BLaZuRE on 2011-12-28
> **inobe said:**
> nvidia

the day they start to suck is the day they stop selling hardware.

I'm not doubting their hardware.  I'm doubting their software.  No doubt if their hardware tanks, they'll tank, but not that many people are on Linux so maybe their drivers could suck for future kernels.

---

### Post by whatthefunk on 2011-12-28
I just bought a Palit GeForce GTX 550 Ti Sonic (Nvidia) and all I had to do to get it working was use the system "search for additional drivers" feature.  No problems so far.

---

### Post by cotcot on 2011-12-28
If you go for nvidia check its compatibility with unity or gnome shell.
I have bad luck. Mine is an nvidia 7300GS and both unity and gnome shell only run on an older nvidia driver. I think that for newer cards there is no problem. 
I cannot advise a lot on ATI because the only card I had started smoking after 1 year.

---

### Post by rubylaser on 2011-12-28
NVIDIA is the way to go.  [VDPAU]("http://en.wikipedia.org/wiki/VDPAU") and simple driver installation makes them a no-brainer for me.

---

### Post by larrypg on 2011-12-28
I have had no problem with the amd card I use.

---

### Post by QIII on 2011-12-28
The same old bash and spread FUD about ATI, I see.  History, folks.  ATI was bought by AMD.  AMD is a member of the Linux Foundation.  NVIDIA?  The fact is that they BOTH produce fine products and, as with anything else, you need to do your homework to decide which one is best for your particular needs.

There is one thing - one - that is different about installing an AMD/ATI driver.  After installing it, before shutting down, you have to do

```
sudo aticonfig --initial
```

to generate the initial xorg.conf.

---

### Post by rubylaser on 2011-12-28
> **QIII said:**
> The same old bash and spread FUD about ATI, I see.  History, folks.  ATI was bought by AMD.  AMD is a member of the Linux Foundation.  NVIDIA?  The fact is that they BOTH produce fine products and, as with anything else, you need to do your homework to decide which one is best for your particular needs.

I rescanned this thread and don't really see any FUD about ATI.  The fact is they are both make nice cards, but if you intend to use an ATI card for hardware h264 video acceleration in Linux, you're currently [SOL]("http://wiki.xbmc.org/?title=Hardware_Accelerated_Video_Decoding#ATI.2FAMD").  ATI's cards are great in Windows for HTPCs and even support bitstreaming HD audio (both NVIDIA and ATI support this in their newer cards).  

If you aren't worried about GPU acceleration for video playback, I'd buy whichever card is cheaper.  For me, NVIDIA has worked well and continues to work well.  I see no reason to change.

---

### Post by wildmanne39 on 2011-12-28
Hi, I have used different nvidia cards for the last five years without problems, but I too have to use an older driver for my card but I do not have any problems because of it.

I even run the cube and effects with no issues in 11.10 but no one can promise there will not be an issue because all computer configurations are a little different.
Thanks

---

### Post by alphacrucis2 on 2011-12-28
My old laptop had an ATI gpu and worked very well with the proprietary fglrx driver. I now have a new Lenovo laptop which has hybrid Intel/NVIDIA graphics, the dreaded optimus arrangement. First I tried bumblebee to get around the problem with optimus but found it rather inconvenient. I found that the Lenovo allows you to disable optimus in the bios so that the OS only sees the nvidia card. The downside is that the power consumption is higher as both graphics hardware are actually running all the time.

So far I have found the NVIDIA to work well. I don't really notice any  difference compared to the old ATI card. I assume the NVIDIA is more grunty being newer and is running a higher res screen. The hardware video decoding mentioned earlier in the thread I guess is a benefit but I have no idea if it is actually being used.

---

### Post by QIII on 2011-12-30
> **rubylaser said:**
> I rescanned this thread and don't really see any FUD about ATI.

I guess that "AMD has bad proprietary drivers that may or may not work well with your videocard." (which is patently untrue) is not FUD.

> but if you intend to use an ATI card for hardware h264 video acceleration in Linux, you're currently [SOL]("http://wiki.xbmc.org/?title=Hardware_Accelerated_Video_Decoding#ATI.2FAMD").

Strangely, clues to the fact that your statement is incorrect are contained in your link.  While it is true that the AMD/ATI drivers don't support hardware acceleration out of the box, they do support H264 hardware acceleration and have since 2009.  Just a bit of extra work and a few commands in the CLI.  Works fine for me.

Both OEMs make good cards and provide solid drivers.  NVIDIA developed VDPAU and jumped on hardware acceleration even before AMD bought ATI.  They got the jump.  But they haven't held their long lead and AMD is breathing down their necks.

I really don't care what people use.  I have machines with both and everything works just fine with both. As I said, one should do their homework and see what suits their needs.  But let's not spread misinformation and zealous brand loyalty.

---

### Post by rubylaser on 2011-12-30
> **QIII said:**
> I guess that "AMD has bad proprietary drivers that may or may not work well with your videocard." (which is patently untrue) is not FUD.

Strangely, clues to the fact that your statement is incorrect are contained in your link.  While it is true that the AMD/ATI drivers don't support hardware acceleration out of the box, they do support H264 hardware acceleration and have since 2009.  Just a bit of extra work and a few commands in the CLI.  Works fine for me.

Both OEMs make good cards and provide solid drivers.  NVIDIA developed VDPAU and jumped on hardware acceleration even before AMD bought ATI.  They got the jump.  But they haven't held their long lead and AMD is breathing down their necks.

I really don't care what people use.  I have machines with both and everything works just fine with both. As I said, one should do their homework and see what suits their needs.  But let's not spread misinformation and zealous brand loyalty.

I missed the has bad proprietary drivers in my read through. That just isn't the case anymore, I'd agree. (I also didn't make this statement, because it's just not true)

But those links do not say that ATI currently does h264 video decoding with the same feature set / ease of setup as VDPAU in Linux ([XvBA]("http://forum.xbmc.org/showthread.php?t=116996") is the closest thing and is not anywhere as easy to setup or does it support the same feature set).  "Could possibly" and "recently announced" don't mean that it's properly working today. I would have bought a 6450 series GPU for my last XBMC HTPC build if was as easy as VDPAU or worked as well. Instead, I went with an NVIDIA 210GT.  It was ~$30 and plays back anything I can throw at it in terms of video.

But, if you're not building a low power HTPC or using CUDA for things like Blender's Cycles renderer (they're working on OpenCL support, so this will work on ATI cards in the future), there's really no reason to pick one over the other anymore other than cost vs. the features you're looking for.

---

