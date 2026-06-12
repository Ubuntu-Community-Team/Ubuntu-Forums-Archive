---
title: "HD stutter"
date: 2010-01-10
forum: Mythbuntu
---

### Post by cedyathome on 2010-01-10
I can't get HD to work. It stutters every second. Any advice is much appreciated.

Software: Mythbuntu 9.10
Hardware : 1.7GHz P4. GE Force 6200 using AGP 4X (nvidia proprietary drivers). Pinnacle 800i HD PCI card. IDE drives. 1.5GB memory

The firmware and drivers are loading correctly. I can use "scan" (dvb utils) to find the channels and "azap" to tune them. SD works fine with no loss of frames in mythtv.

I've made all the hardware/driver tweaks recommended in
[http://www.mythtv.org/wiki/Optimizing_Performance](http://www.mythtv.org/wiki/Optimizing_Performance)

Am I just wasting my time with this hardware?
Anyone have first hand knowledge of making HD work on similar configuration?

Thanks in advance.

---

### Post by bobbob1016 on 2010-01-10
It would help if I knew the actual model number of your video card, but if you have the proprietary drivers, it might help to use VDPAU.  Mplayer and mythtv both have settings for it.  Try "mplayer -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau /path/to/HD/file" and I think the setting for mythtv is in the TV Settings option.  If you use mplayer in mythtv, use this line "mplayer -vo vdpau -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau -fs %s" as your mplayer command option.

Edit:  Some older NVidia cards can't do VDPAU, not sure if more recent AGP cards can do VDPAU, but a PCIe should be able to.  My AspireRevo with an Atom 1.6ghz and an nvidia ion (9600 iirc) can do 1080p without a stutter (and +/- 10% CPU) using VDPAU.

---

### Post by cascade9 on 2010-01-10
> **bobbob1016 said:**
> Edit:  Some older NVidia cards can't do VDPAU, not sure if more recent AGP cards can do VDPAU, but a PCIe should be able to.  My AspireRevo with an Atom 1.6ghz and an nvidia ion (9600 iirc) can do 1080p without a stutter (and +/- 10% CPU) using VDPAU.

Its a 6200.....and no, it cant do VDPAU. In fact, no AGP nVidia card can do VDPAU- the last series of AGP cards nVidia put out as 7xxx and they dont support VDPAU.- 

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

There is only 1 motherboard I know of that has AGP and PCI-E sots, and that was AMD so I doubt that there will be a PCI-E slot to use

If I recall correctly, you need minimum of 2.4-2.5Ghz for a single core CPU to run HD without stuttering (without some form of hardware decoding that is). 

But wait, there is hope!  :mrgreen:

You could get a nice, cheap PCI 8400GS nVidia card. Supports VDPAU, and people here have used VDPAU to play HD video on machines with similar amounts of CPU power to the P4 1.7.

---

### Post by cedyathome on 2010-01-10
Thank you.

The video card is from Zotac and based on the GE Force 6200 which doesn't support VDPAU. 

There is no PCI express slot on this board which is why I had to go with the 6200. It was the latest nvidia chip that I could find with a 4X AGP interface.

My computer is a Compaq Presario 5330US and I was hoping to re-purpose it as a PVR.

I would really appreciate your opinion on the hardware or on any tuning sites. I've spent 3 days looking all over the web for ideas on how to tune this to work.

---

### Post by bobbob1016 on 2010-01-10
I don't think it'll work well, my old P4 3.4ghz HyperThreaded wouldn't do HD either, I think you need an Intel CoreDuo or AMD equivalent, since they have faster bus speeds, or something like that.[http://www.logicsupply.com/products/bcm970012](http://www.logicsupply.com/products/bcm970012) but that is PCIe, I think there is a PCI one as well.

---

### Post by cedyathome on 2010-01-10
> **cascade9 said:**
> 
You could get a nice, cheap PCI 8400GS nVidia card. Supports VDPAU, and people here have used VDPAU to play HD video on machines with similar amounts of CPU power to the P4 1.7.

This is the only card 8400 card with a PCI interface that I could find at newegg.com. Any experience with it? I'm willing to try it.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814187042](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187042)

---

### Post by cedyathome on 2010-01-10
I've found a new wrinkle.

If I use mythtv in LiveTV mode on an HD channel, the stutter is really bad. (as mentioned in my original post)

If I set mythtv to record an HD channel, and play the mpeg file using VLC while it is being recorded, the stutter is still there but not as bad.

If I wait after the recording, the stutter is very much reduced.  There are no issues while playing the recording on my CoreDUO notebook, so the recording is fine.

The better graphic card may do the trick. I'm hoping I don't run into PCI bus contention between  my tuner (Pinnacle 800i PCI) and the new graphics card ([GE Force 8400 PCI]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187042")).

Any advice / insights? 

Thank you.

(my wife says go ahead and get the card. Chalk it down to the cost of learning stuff. Picking myself off the floor)

---

### Post by yonkiman on 2010-01-10
Live TV doesn't get as much love from the developers as playing back recorded programs, so it's sometimes lower performance/glitchier.  I don't channel surf, so it rarely bothers me.

While a program is recording, a lot is going on, including (obviously) writing the show to the hard disk.  This eats into some of the system bandwidth needed to play it back and decode it.  And if you have other options on (like starting commercial detection as soon as the recording starts), that will further eat into your I/O and CPU bandwith.

If you wait until the show has been recorded and all post-processing (commercial detection, transcoding) is complete, the loading will be as low as it's going to get.

I believes that explains what you're seeing...

Here's the wiki that has some ideas on how to improve performance:
[http://www.mythtv.org/wiki/Optimizing_Performance](http://www.mythtv.org/wiki/Optimizing_Performance)

---

### Post by tgalati4 on 2010-01-11
cat /proc/interrupts

Look for high numbers of interrupts while playing HD.  Also look for any devices that share an interrupt.  That could also cause stuttering.  I agree, P4 is marginal for HD.  Intel pushed the Pentium D (dual core) with it's VIIV campaign, but it can't handle HD either.  So much for Intel's plan to litter the world with VIIV-enabled devices.  I use the T-shirt for painting, and I still have the coffee mug.

---

### Post by cascade9 on 2010-01-11
> **bobbob1016 said:**
> I don't think it'll work well, my old P4 3.4ghz HyperThreaded wouldn't do HD either, I think you need an Intel CoreDuo or AMD equivalent, since they have faster bus speeds, or something like that.[http://www.logicsupply.com/products/bcm970012](http://www.logicsupply.com/products/bcm970012) but that is PCIe, I think there is a PCI one as well.

Correction from my previous post- from doing a look around, is seems you need 3.6Ghz (single core) or 2.4-2.5 Ghz (dual core) to get smooth playback with HD. 

HD does vary though, 720p is less demanding than 1080p..and even then requirements will vary, depending on how 'complex' the HD content is (e.g. a black screen @ 1080p is going to use a lot less decoding power than a multicolour fight scene in 1080p) 

> **cedyathome said:**
> I've found a new wrinkle.

If I use mythtv in LiveTV mode on an HD channel, the stutter is really bad. (as mentioned in my original post)

If I set mythtv to record an HD channel, and play the mpeg file using VLC while it is being recorded, the stutter is still there but not as bad.

If I wait after the recording, the stutter is very much reduced. There are no issues while playing the recording on my CoreDUO notebook, so the recording is fine.

The better graphic card may do the trick. I'm hoping I don't run into PCI bus contention between my tuner (Pinnacle 800i PCI) and the new graphics card ([GE Force 8400 PCI]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187042")).

Any advice / insights? 

Thank you.

(my wife says go ahead and get the card. Chalk it down to the cost of learning stuff. Picking myself off the floor)

I'd guess that LiveTV mode uses the most CPU, and for some reason playing it back using VLC uses less. Obviously, playing after recording uses the last CPU (as your only playing a file, not recording/playing at the same time)

You shouldnt have any issues with the PCI bus, its 133MB/sec (in theory, reality is probably lower than that). 

Once you have the card, your CPU use (for playback) should drop a lot, and the stutter should go away. Its possible that some things will still get stutter, as not every codec is supported under VDPAU, and its also possible that 1080p might still stutter but 720p will be fine.....its worth the risk well IMO. 

Good luck. ;)

---

### Post by cedyathome on 2010-01-13
Thank you all for your replies. After looking at your responses and information I've read elsewhere, I have decided against buying an nvidia GEForce 8400 card & instead, I'm going to upgrade my PC to a dual-core CPU. That will get me better drives, memory access, pci-X  etc. Now, to go earn that extra money!

---

