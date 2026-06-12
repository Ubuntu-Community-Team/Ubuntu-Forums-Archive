---
title: "Hauppauge HD-PVR Install Question"
date: 2009-12-30
forum: Mythbuntu
---

### Post by yonkiman on 2009-12-30
Santa gave me an HD-PVR!  But I'm confused by this part of the instructions on [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR) :

> Note: As of Linux Kernel 2.6.30 the driver for the HD-PVR is now included by default. No compiling of the driver will be necessary assuming you have compiled the driver into the kernel. 

"No compiling of the driver will be necessary assuming you have compiled the driver"  ????

I'm running 2.6.31-16-generic...do I need to compile anything?

Cheers.

---

### Post by jquintana on 2010-01-20
Were you able to get your HD-PVR to work?

---

### Post by yonkiman on 2010-01-20
> **jquintana said:**
> Were you able to get your HD-PVR to work

Yes!  I just tried it and it basically worked immediately.  The main thing that took a bit of time to work out was using mythchanger to change the channels of the HD-PVR over firewire, but ultimately, once I'd compiled the latest mythchanger, even that was as simple as putting "mythchanger - c " in the appropriate box of mythbackend-setup.

One thing I haven't seen people mention before is how incredibly good the HD-PVR hardware is.  I was pretty dismayed to have to use this solution - the idea of the program arriving as compressed digital, being decompressed and converted to analog component video, then being converted back to digital and recompressed sounded terrible to me.  There are all sorts of analog errors and compression artifacts that could (and I expected some would) be introduced.  

But the image quality is frankly amazing.  Blacks look good (not clipped or too light as you might get with an analog offset in the YPbPr), and even when I look critically I don't see compression artifacts except for extremely fast pans (when you always see compression artifacts).  And the icing on the cake is that the file size for an HD program is *smaller* than the file size for the SD version of the same program recorded on my old PVR-150!  Amazing!

It's working so much better than I expected!  Good job Hauppauge!  And MythTV team, for making the installation of it much easier than I expected.  Amazing work all around!

---

### Post by dolson on 2010-03-16
I am considering picking one of these up, but I can't seem to find any real info about system specs. I did see one comment about needing a dual core and a GPU with 256MB VRAM - is this the case even under Linux? My PCs are all outdated, and I'd rather not order a $220 useless capture tool before upgrading my PCs.

All I really want to do with it is record PS3 gameplay footage at 720p with stereo audio.

---

### Post by aovermy on 2010-03-16
One thing I've noticed with my HDPVR (also a holiday present) is that sometimes synch between the picture and the sound gets off. I've seen the problem twice now, once in a drama and once in a cartoon. I have the component and the optical sound connexion hooked up so I suspect that my problem is my receiver's configuration--possibly it's sending borked audio on occasion.

---

### Post by aovermy on 2010-03-16
> **dolson said:**
> I am considering picking one of these up, but I can't seem to find any real info about system specs. I did see one comment about needing a dual core and a GPU with 256MB VRAM - is this the case even under Linux? My PCs are all outdated, and I'd rather not order a $220 useless capture tool before upgrading my PCs.

All I really want to do with it is record PS3 gameplay footage at 720p with stereo audio.

The hardware requirements are for playback, not capture. Because all the compression/formatting is handled by the HDPVR itself, recording takes very little mainboard CPU. Playback, on the otherhand, takes quite a bit. I record at 1080i and my dual core (1800 per core) laptop can't handle playback. My dual core 4600 desktop has no problem though and my AMD Geode NX(1650Mhz single core if I recall) based frontend is only able to handle it due to the Nvidia GS8600 PCI card and the magic of VDPAU on Linux.

---

### Post by dolson on 2010-03-16
> **aovermy said:**
> The hardware requirements are for playback, not capture. Because all the compression/formatting is handled by the HDPVR itself, recording takes very little mainboard CPU. Playback, on the otherhand, takes quite a bit. I record at 1080i and my dual core (1800 per core) laptop can't handle playback. My dual core 4600 desktop has no problem though and my AMD Geode NX(1650Mhz single core if I recall) based frontend is only able to handle it due to the Nvidia GS8600 PCI card and the magic of VDPAU on Linux.

Can I still see what I am doing while capturing, then? I assume I could use the output ports for pass-thru video, and plug that into a monitor/TV, right?

Maybe I will order it, then.

---

### Post by phroman on 2010-03-24
Hi Yonkiman, a question for you:

> The main thing that took a bit of time to work out was using mythchanger to change the channels of the HD-PVR over firewire..

Are you tuning an antenne for over the air reception?  Wouldn't you be tuning a satellite or cable box?

---

