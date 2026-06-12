---
title: "Video Lags/Stutters when Watching HD OTA"
date: 2011-01-31
forum: Mythbuntu
---

### Post by prof3205 on 2011-01-31
Good Evening All,

Got a problem that should be an easy solve, but I just can't seem to get a handle on it.

Seems like after installing almost any version of Mythbuntu (9.04, 9.10, 10.04 and 10.10), when trying to watch over the air HD stations, the video and sound lags/stutters (I'm not sure is that's a good enough description ... but it seems like the computer can't keep up).  When I watch and SD station (the few that are left in the LA area) everything seems fine.

I've used "top" top check CPU usage.  When watching SD, the CPU is at about 52%-54% and when watching HD, it gets up to about 67-69%.

Here's the specs on my computer:
Dell Dimension GX280
   2.4GHz Pentium 4 CPU
   2GB PC2100 DDR memory
   nVidia GeForce 4 AGP w/64MB memory (would a 256MB PCI card be better???)
   120GB EIDE Hard Drive (7200RPM / 2MB cache)

The computer also has MB-based video, but I'm sure that would be worse performance.

I can't believe that the CPU is too slow or I don't have enough memory (but that's possible) to watch HD OTA.  I've read a few comments that there should be an ATSC setting in the "Backend Setup/General/Locale", but all I see is NTSC.  Could that be the problem, and if so, how you get the ATSC option?

Any hope here???

Thanks in advance.

---

### Post by prof3205 on 2011-01-31
Me Again,

Sorry, I forgot to say that I've tried it with an HDHomeRun HD box and a Hauppauge HVR-1600 capture card, both support OTA digital signals.

Thanks.

---

### Post by nickrout on 2011-01-31
your system simply is not powerful enough.

---

### Post by cascade9 on 2011-01-31
> **prof3205 said:**
> I can't believe that the CPU is too slow or I don't have enough memory (but that's possible) to watch HD OTA.

Believe it- 

> **Minimum Requirements** for Running** 1080p **on** PC**:
 **A. **The minimum requirements to play FullHD content on PC are pretty high, with a standard [Codec]("http://en.wikipedia.org/wiki/Codec").
 *Processor***: 2.4Ghz** (dual core) or **3.5Ghz** (single Core) processor.
 *Graphics*: **Nvidia/ATi** having bare minimum **256MB Video RAM **and **core clock 600Mhz. **
 When you try to play it in a lower config PC, the video plays but is often jerky.
[http://www.taranfx.com/1080p-minimum-requirements](http://www.taranfx.com/1080p-minimum-requirements)

Thats not a exact set of requirements (what one system will play another with similar hardware but different software might not play). BTW, forget the video requirements listed there, with enough CPUpower or VDPAU cards with less than 600MHz core clock can play HD fine). 

There might be a solution though. According to dell, your computer has PCIe slots- 

[http://support.dell.com/support/edocs/systems/opgx280/en/ug/specs02.htm](http://support.dell.com/support/edocs/systems/opgx280/en/ug/specs02.htm)

A PCIe nvida card (I'd get a GT210/220/430) and VDPAU (nvidia hardware video decoding should play HD on your system without . 

If you system only has an AGP slot and DDR1, its not a GX280 from what dell says, and you would need to get a new system to play HD.

---

### Post by nickrout on 2011-01-31
> **cascade9 said:**
> Believe it- 

[http://www.taranfx.com/1080p-minimum-requirements](http://www.taranfx.com/1080p-minimum-requirements)

Thats not a exact set of requirements (what one system will play another with similar hardware but different software might not play). BTW, forget the video requirements listed there, with enough CPUpower or VDPAU cards with less than 600MHz core clock can play HD fine). 

There might be a solution though. According to dell, your computer has PCIe slots- 

[http://support.dell.com/support/edocs/systems/opgx280/en/ug/specs02.htm](http://support.dell.com/support/edocs/systems/opgx280/en/ug/specs02.htm)

A PCIe nvida card (I'd get a GT210/220/430) and VDPAU (nvidia hardware video decoding should play HD on your system without . 

If you system only has an AGP slot and DDR1, its not a GX280 from what dell says, and you would need to get a new system to play HD.

Or a PCI vdpau capable graphics card

---

### Post by cascade9 on 2011-01-31
> **nickrout said:**
> Or a PCI vdpau capable graphics card

8400GSes have been known to have nasty issues on intel 845 chipsets (and 865 IIRC). Which if it isnt a GX280 is probably the chipsets its most likely to have.

---

### Post by ubuntu1sttimer on 2011-02-01
If I may, I would like to offer a different idea on this. This may or may not be your problem but it could help others reading this thread in the future.

Digital television is different than the old analog that we are used to. With analog you could watch a station that had a weak signal or possibility power line or other interference. Your mind just adjusted to the problem and you "got by". Digital signals have packets of information along with a check sum to verify that the packet is good. Much like network packets except that there is no way for you to request a resend of a bad packet from a TV station. Thus you get a broken picture when there is a lost packet. And with digital TV you don't get to see what the problem is, only a broken or no picture.

To further complicate the problem, the idea that you are watching channel 6 for example is that now they can make any channel appear to be channel 6 to the viewer. For example, I am aware of one station that was on VHF channel 6 for many years. Now with digital TV they were moved to UHF channel 35. They still use the old TV6 logos and few people know what happened. To add to the problem, UHF channels take a very different antenna than VHF channels. Some antennas are designed to serve both but not all. One thing that seems to be the case is that most of the VHF stations that have changed channels went to UHF.

Now, if you want to have the best chances of getting a steady picture, you need a good antenna. Even when the station is not too far away. Digital signals do not play well with signal reflections that with analog TV used to show up as fringing around the elements of the picture. Also, if the signal is a weak, the digital receiver will drop in and out of lock with the picture doing the same. 

And if all that is not enough, there is a great difference in receiver quality. For example, my big flat screen receiver has a lousy signal reception section. Some channels just don't come in all the time. I also have a cheap digital to analog converter box that when connected to the same antenna lead easily gets all the channels the expensive set can, plus some more.

Lastly, regarding antennas, if you can, use a good one located outside and pointed toward the desired stations. In my case I have to different directions for stations located in different directions. I have two quality antennas, each with a preamplifier and coax cable to the set. The down side is that I have to have a switch to select the direction I want to watch.

This has been a long message but I hope it will help someone that is getting frustrated with their efforts with digital off the air reception either via a computer card or a regular TV receiver.

Lastly, I have a Hauppauge HVR-1600 that I have tried to get going on Ubuntu without any luck. But then, it does not work well on Windows either so I have about given up on it.

---

### Post by newlinux on 2011-02-01
One more thought - your video card probably supports XvMC which is hardware acceleration for older nvidia cards and mpeg-2 recordings. It is not without problems, but I used to use it pretty reliably. You might look into using XvMC if you don't want to upgrade.

I used to use a a computer pretty much spec'd with the same GPU with a 440MX AGP vid card successfully to watch mpeg-2 720p/1080i (which is what you'll get HD OTA) with XvMC.
[http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)

---

### Post by nickrout on 2011-02-02
> **newlinux said:**
> One more thought - your video card probably supports XvMC which is hardware acceleration for older nvidia cards and mpeg-2 recordings. It is not without problems, but I used to use it pretty reliably. You might look into using XvMC if you don't want to upgrade.

I used to use a a computer pretty much spec'd with the same GPU with a 440MX AGP vid card successfully to watch mpeg-2 720p/1080i (which is what you'll get HD OTA) with XvMC.
[http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)

Except, mythbuntu no longer supports xvmc and does not compile xvmc support into it's builds any longer.

What's more mythtv as a whole will no longer support xvmc from 0.25 onwards.

Also, I don't know that xvmc has ever been supported on a 440MX. However I find the nvidia readme to be a little unfathomable on this subject.

---

### Post by newlinux on 2011-02-03
> **nickrout said:**
> Except, mythbuntu no longer supports xvmc and does not compile xvmc support into it's builds any longer.

What's more mythtv as a whole will no longer support xvmc from 0.25 onwards.

Also, I don't know that xvmc has ever been supported on a 440MX. However I find the nvidia readme to be a little unfathomable on this subject.

well - so much for that idea, unless you want to compile mythtv yourself :).

However, I'm sure I ran xvmc on my 440MX, so I know it supported it.

---

