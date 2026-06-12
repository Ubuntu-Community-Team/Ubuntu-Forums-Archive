---
title: "MythTV hardware upgrade recommendations"
date: 2008-09-27
forum: Multimedia Software
---

### Post by poe503 on 2008-09-27
After installing an ATSC (digital) tuner, I find that my old P4 3ghz, 800fsb system can barely handle an HD broadcast even when I remove as much CPU load as is possible.

I am looking to upgrade and would appreciate hearing other's experience in building a reasonably priced system to handle HD.

Ideally I would like a system that would be able to handle recording 2 HD broadcasts with commercial cutting and HD playback simultaneously. 

Please share. Thanks.

---

### Post by poe503 on 2008-09-28
Would a dual core do the job or is a quad necessary?

---

### Post by dhughes on 2008-09-28
I'm thinking (again) of building a Myth setup and from what I've read a P4 3GHz should be more than enough to have a good stable system. The specs of a TiVo are far less than P4 3GHz, then again you are using HD.

 Just my 2 cents, and a bump.

---

### Post by poe503 on 2008-09-28
Thanks for the reply and bump.  

My system was plenty fine at P4 2.4ghz with my Pvr150s and analog broadcasts. I swapped CPUs when I went digital.

While I can get a stable HD recording with my new tuner, I have to unload playback onto the GPU and do commercial cutting after recording or I get freeze ups, jitters, and screwed up commercial cuts.  

The system monitor shows the CPU is working at nearly 100% when I playback some broadcasts.  It works at 50% on other broadcasts.

I have read that my 3.0ghz system is considered to be minimum for HD and my experience shows that to be true.

The playback is excellent and well worth going to ATSC.

---

### Post by Bakon Jarser on 2008-09-28
I was interested too so I thought I'd list some relevant links.

[http://ubuntuforums.org/showthread.php?t=886656](http://ubuntuforums.org/showthread.php?t=886656)

[http://ubuntuforums.org/showthread.php?t=882105](http://ubuntuforums.org/showthread.php?t=882105)

[http://ubuntuforums.org/showthread.php?t=876977](http://ubuntuforums.org/showthread.php?t=876977)

---

### Post by poe503 on 2008-09-29
Thanks for the links. :)

I found the last one to be particularly informative.

I must have missed it when searching. The right keyword makes all the difference.

---

### Post by Bakon Jarser on 2008-09-29
Actually advanced search > search thread titles only is what makes all the difference.  I wish they would make it default.

---

### Post by markbuntu on 2008-09-29
What you should really get,
the fastest quad core cpu you can find
mobo with 4 pcix16 slots, ddr3ram 16GB
4 ATI HD4870 1GB cards in crossfire pairs
2 24 inch monitors for native 1920x1080p HD rendering

---

### Post by Bakon Jarser on 2008-09-29
lmao.  Sure, I'll go to the bank and apply for a loan right now.:D

---

### Post by poe503 on 2008-09-30
> **markbuntu said:**
> What you should really get,
the fastest quad core cpu you can find
mobo with 4 pcix16 slots, ddr3ram 16GB
4 ATI HD4870 1GB cards in crossfire pairs
2 24 inch monitors for native 1920x1080p HD rendering


Yow,a yacht!  I like the cut of your jib, mate.  Alas, I'm on a rowboat budget. :(

---

### Post by markbuntu on 2008-09-30
Well, You asked for it. Anyway you should really consider a HD4850 card and a 24 inch monitor. The card has hardware support for 1080p and the 24 inch monitor is the smallest monitor with native 1080p. 

A smaller monitor will mean the gpu must work harder and will be slowed down as it converts the 1080p signal to fit. I got a nice 24 inch 2ms monitor for $300. The HD4850 runs around $120 or less these days or will be soon, a price drop is expected. A fast dual core cpu and 4GB ram will also help a lot. And go with SATA drives, they are far faster than PATA drives and cost the same.

I would consider these as minimums for HD production. They will make your life so much easier for about $7-800.

---

### Post by noisymime on 2008-10-02
poe503 after doing a HUGE amount of research, here are my conclusions:
**CPU:** Buy the fastest dual core you can afford (~3Ghz). Quad core provides next to no advantage as the decoding for h.264 (The codec that needs to most power) isn't multithreaded enough to take advantage of it. It requires high clock speed rather than multiple cores to run well. Quads also cost more, use more power and generate more heat.
**Video Card:** Doesn't matter what you get really. None of the current model nVidia cards provide XvMC support and (no matter what anyone tells you) there is currently NO consumer cards that do bluray/h.264 hardware decoding in linux. I recommend getting a motherboard with onboard DVI/HDMI output, that way you can upgrade later when Intel/nVidia/ATI start offering HD hardware support.
**RAM:** PC6400 at least. 2gb should be plenty

If you want to play it a little bit risky (and you're buying an Intel CPU), get a board with the G45 chipset. Its a little flaky in linux at the moment, but I think its the best chance of getting hardware h.264 decoding in the future.

As for price, I just bought the following:
Intel E8500 (3.16Ghz)
4gb HyperX PC6400 ram
Gigabyte G45 motherboard (Built in DVI and HDMI outputs)

Cost me $460 AUD which is about $365 USD at the moment. Seems like a good deal to me.

---

### Post by poe503 on 2008-10-08
Noisymime, thanks for your input, sorry for my tardy reply.  

I would remark that concern regarding h.264 isn't a factor here in the US as the adopted ATSC standard doesn't include it (as far as I know).

Cheers. Poe.

---

### Post by noisymime on 2008-10-08
> **poe503 said:**
> 
I would remark that concern regarding h.264 isn't a factor here in the US as the adopted ATSC standard doesn't include it (as far as I know).

No problems, we're the same in Australia (HDTV is MPEG2).

However the one thing you may want to consider on the h.264 side of things is if you think you might ever use BluRay or one of the HD download services. These all use h.264.

---

### Post by markbuntu on 2008-10-09
ATI has promised to have their linux drivers up to par with their windows drivers by early next year. I imagine this will include blue-ray and h.264 support.

---

