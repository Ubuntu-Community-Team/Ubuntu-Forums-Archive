---
title: "ATI HD video support"
date: 2011-07-12
forum: Multimedia Software
---

### Post by SeijiSensei on 2011-07-12
I'm looking at new laptops for my daughter.  In the past I would simply stick to NVIDIA for these purchases since I wanted to use VDPAU for video in Linux.  However the Optimus fiasco has made that a non-starter. (Are you listening, NVIDIA?)  So I've started to consider Radeon's instead. (Intel cards are out since she'll be playing a few Windows games on this machine like Dragon Age that won't work with Intel cards.)

So I need a bit of advice.  The cheapest machine we're looking at runs an i3, so perhaps that alone is sufficient to handle H.264 decoding of 720p (and maybe 1080p) content without passing it off to the video adapter.  However I've heard rumors that the most recent proprietary drivers for ATI cards are competitive with NVIDIA/VDPAU for video.  Is that true?  Does it even matter if we're using an i3 or i5 CPU?

For reference, [one machine we're considering]("http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:item.detail?GroupID=243&Code=439522U") has an ATI Mobility Radeon HD 6550M with 1GB.

What's the level of support for VAAPI in media players like mplayer?

---

### Post by BicyclerBoy on 2011-07-12
Optimus:
AFAIK there are at least (2) forms of optimus. The differences are around the framebuffer mux.
Some h/w allows the nVidia graphics to use the framebuffer without having to use the intel GPU. i.e. works easily with linux as nVidia only GPU.

Decode performance:
My core2duo can decode (1) video 1080i (OTA broadcast) at 50% while using VDPAU to decode/presentation of a 2nd stream.
(not using any post decode filters on CPU except yadif)

Intel:
The i3 is approx 2x the performance of core2duo.
The i5 is better because of L3 cache.
Sandybridge is better again & the GPU is better.
The intel thermal efficiency is unmatched..

AMD:
The zacate/fusion AMD APU should make a good netbook.
The Llano/fusion APU might make a notebook.
But again the AMD drivers are letting it down.
AMD published the XvBA API specs ?? only in Feb this year..so 3 years after nVidia.

VA-API:
I don't use so below is best guess.
currently is a subset of VDPAU capabilities.
Probably fine except for HTPC.
There is a "VDPAU backend for VA-API" library.
VLC can use VA-API directly.
VA-API on XvBA only does mpeg-4/10 (H264) & wmv9 (VC-1) & no de-interlacing.
[http://www.splitted-desktop.com/~gbeauchesne/]("http://www.splitted-desktop.com/%7Egbeauchesne/")

Non-conclusion:
One would hope that intel sandybridge solution is more than good enough especially for a laptop.
At least intel supports open source whereas nVidia does not (but the drivers do work).
AMD doesn't seem to do either (open or work)..

---

### Post by SeijiSensei on 2011-07-15
I'm going to bump this in hopes of getting some more replies.  BicyclerBoy's response is pretty negative.  Is that the consensus of opinion on ATI and HD video, with or without VAAPI?

> **BicyclerBoy said:**
> Optimus:
AFAIK there are at least (2) forms of optimus. The differences are around the framebuffer mux.
Some h/w allows the nVidia graphics to use the framebuffer without having to use the intel GPU. i.e. works easily with linux as nVidia only GPU.

From what I've read, recent machines all ship with the version of Optimus that always uses the Intel chip, and thus isn't compatible with Linux.  I don't even know how I would be able to tell which Optimus version I'd be getting just from reading product specs.

---

### Post by Grenage on 2011-07-15
I have an ATI card in my XBMC machine, and it does handle the video reasonably well.  Looking at the output, the ATI card handles about 60% of the decoding, and the processors take care of the rest.  I'm not sure if it's automatically balancing, or if the ATI card can't handle more.

I would obviously have chosen an nvidia over an ATI, but it came free with the machine.  Most modern processors can handle 1080p rather well, should graphical support be lacking.  My old Core2Due is fine on 720, but not 1080p.

---

### Post by BicyclerBoy on 2011-07-15
Sorry about the negativity..
To get a view of how Optimus is working with Linux..check out
deBumblebee or vgaswitcharoo projects..
Beware there are AMD "optimus" graphics solution out there too...

An i3 or i5 CPU/GPU laptop can easily do H264 decode in CPU (~25% load).
The GPU is almost relevant except for battery life.
But no x86 CPU comes close to sandybridge variants for power & efficiency.

---

### Post by Eromatic on 2011-07-21
On my ATI card, I prefer to use the GL renderer on SMPlayer. VA-API has always been a hit or miss depending on how the video had been encoded. Better to have the fast CPU to do the decoding.

[http://www.youtube.com/watch?v=q1Zls7fwfzg](http://www.youtube.com/watch?v=q1Zls7fwfzg)

---

### Post by .... on 2011-07-22
Note that the machine you link to also has hybrid graphics, so it's not better than an Optimus machine. Be careful!

---

### Post by SeijiSensei on 2011-07-22
We ended up ordering an [HP dv6tse]("http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=High+performance&series_name=dv6tse_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/High_performance/dv6tse_series") with a Radeon 6770M video card. As my daughter is a college student, we got a pretty good deal on this machine.  (She prefers Linux to Windows, but her campus's proprietary wifi network doesn't support Linux.  So, in reality, she spends most of her time in Windows while at school.)  The computer should be here in a couple of weeks.  I'll post again here after I've had some time to try it out with Ubuntu.

It seems well nigh impossible to buy a notebook these days that doesn't come with hybrid graphics unless you're buying a pure Intel device.  From my limited understanding, it's easier to switch between the Intel and ATI cards than between Intel and NVIDIA using Optimus.  Apparently Optimus uses the NVIDIA card as a pre-processor then pushes the signal through the Intel chip for eventual display.  (Windows gamers have had problems with this combination as well; the game installers sometimes can't see anything other than the Intel card and refuse to install.)  From what I've read about Intel/ATI hybrids, only one of the chips is in use.  I'm curious to see how switching can be handled in this case.  As I say, I'll let you know.

---

