---
title: "VIA EPIA M10000G Mini-ITX: Does It Have What It Takes To Render HD Video?"
date: 2009-01-05
forum: Mythbuntu
---

### Post by PeteCress on 2009-01-05
Came across what I think is a nicely-written page on building a mini-myth box at [http://tinyurl.com/7nzxvy](http://tinyurl.com/7nzxvy).

But after investing some hours I haired out on the minimyth.config file.

But then I realized that MiniMyth was probably predicated on a 1-gig CF card being the biggest affordable solution... and that 4-gig CF cards had gotten a lot cheaper than when that page was written.

On the way home from work today, I bought a 4-gigger (SanDisk Ultra II, $29.95 at Circuit City).

Successfully installed Ubuntu 8.04 and the regular MythTV front end on it and it's running ok in an old Athlon box rescued from the dumpster - except that HD videos are too uneven to watch.   Regular-def is a-ok, but HD just doesn't cut it.   *Very* old nVidia video card.   Also tried a not-quite-so-old dual-head Radeon 7000 or 9000 - same result. 

End game is to build a MythTV front end box with no moving parts.

Seems like the 4-gig CF card running in the Athlon is proof-of-concept drive-wise as long as I can set up the system so it doesn't hammer the CF card's bits into early oblivion.

The motherboard of choice for the author of the abovementioned page was VIA's ME6000 (as shown at [http://tinyurl.com/pzsth](http://tinyurl.com/pzsth)).

It's claim to fame seems tb that it has an onboard MPEG2 decoder, so that the lack of CPU power isn't a problem when rendering video.

My question: will VIA's ME 6000 render HD video smoothly?   

I'm thinking that page may have been written a few years ago and be predicated on non-HD rendering.

---

### Post by ttabbal on 2009-01-07
I have an old ME6000 floating around. I have considered getting the fanless NVidia PCI 8400 card and attempting to use VDPAU for playback. My X2 3800+ uses less than 10% CPU when I'm using the patched mplayer. I haven't wanted to switch to Myth Trunk yet though, so I couldn't use the Myth internal player for anything on that box. 

I doubt the VIA chips have what it takes for HD in CPU. What resolution, codec and bitrate are you trying to use? MPEG2 720p might be possible with your board.

---

### Post by ozybushwalker on 2009-01-09
I have a few different mini-ITX boards with VIA CPUs and chipsets.

To run Mythbuntu 8.04 or later the CPU must have the CMOV instruction. Some C3 CPUs do and some don't. The 1GHz Nehemiah does but the 800MHz Samuel doesn't. I expect C7 CPUs would have CMOV. I don't know about the CPU on either the M6000 or M10000G board.

There doesn't seem to be Linux software support for the HDTV enabling capabilities in any of the VIA chipsets: see [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=HardwareCaveats"). Therefore to play HDTV you would need a HDTV capable PCI video card. Using XvMC I have been able to get standard definition digital TV to play well on a system with 1GHz VIA C3 and CLE-266 chipset.

---

### Post by PeteCress on 2009-01-14
Sounds to me like I ought to put this on the back burner for awhile.

The agenda is to build two or three boxes that can be put underneath a television set, make zero noise, hook into the home LAN, and render MPEG from MythTV.

Also, my guess is that they'd often be left turned on 24-7... so the low power requirement of a fanless board would have additional benefit.

Not positive what my requirements are HD-Def-Wise.... but I'd think I want the max bc I don't know enough about MythTV to make it transcode or save in anything except whatever the program came in at.

Maybe I'm just hoping, but it seems to me like the convergence of PC and TV is a work in progress - early progress.... which should accelerate once the country's non-cable-non-dish users really get into digital TV sets....

Anybody have thoughts on this?

---

### Post by Archmage on 2009-01-14
There are a few fanless systems out there, but as far as I see none is supporting HDTV under Linux.

But I assume that this change in the near future.

---

### Post by AHanff on 2009-01-14
NVidia Ion platform - not available yet but will be soon - just hope it is well priced.  Uses the 9400 integrated GPU which can do full 1080p HD without even breaking a sweat.

---

