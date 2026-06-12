---
title: "Media Center PC"
date: 2014-03-26
forum: Multimedia Software
---

### Post by momspcs on 2014-03-26
I want to build an Ubuntu Media Center PC to stream (netflix)movies, (epsn)sports, etc. over the internet and recieve digital TV over the air.
I have built 4 Ubuntu machines in the past. All four times I have had difficulty finding the proper video drivers. 
Can someone recommend  a hardware recipe that has Ubuntu drivers readily available??? Motherboard, Processor, Video, Sound, etc.??

Thanks,

---

### Post by TheFu on 2014-03-26
Any content with DRM will be problematic. That isn't to say that you cannot make it work, just that you shouldn't expect it to work out-of-the-box.
Depending on what you need the PC to do, different hardware will be recommended. I have an AMD E-350 APU that handles playback. It was $150 total. It isn't powerful enough to transcode content on-the-fly for other playback devices, so if you need that, then get a new Core i5/i7.  For recording, I have assigned 2 CPUs inside a KVM virtual machine connected to fast HDDs and 4 network OTA tuners.  This VM runs on a Core i5 that does all sorts of other things all the time too. I like having the TV recording part virtualized - easier to migrate to the next machine when that day comes, plus backups are bonehead simple - which I need for Windows stuff.

As far as video cards go - any card made in the last 4 yrs is fine - $20 is enough for video playback at 1080p.  Heck, my E-350 box has onboard ATI 54xx GPU and it handles playback great!  Plus it is silent, except the 4TB HDD spinning. No fans at all.

Streaming is more about having a solid connection too. Wifi streaming is hit-or-miss. If your wifi router is across the house, invest in power-line networking. Even crappy powerline is better than wifi usually. Wired ethernet blows both of those away for a consistent connection.

So - if you really want the best references for hardware - check out the mythtv forums.  I can completely recommend the HD Homerun OTA tuners. Best available, they completely rock.  I have 2, for a total of 4 tuners. Extremely popular and they work well. I can't believe all the time I wasted on PCI and USB tuner cards. Never again.

---

### Post by Yellow Pasque on 2014-03-29
> **TheFu said:**
> As far as video cards go - any card made in the last 4 yrs is fine

Disagree. Avoid Intel Atoms with Cedarview (GMA3650) graphics like the plague.

---

