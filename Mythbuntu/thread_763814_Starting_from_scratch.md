---
title: "Starting from scratch"
date: 2008-04-23
forum: Mythbuntu
---

### Post by bah1976 on 2008-04-23
This is my first venture into the linux world, as well as building my own DVR, and I have some questions before I invest in hardware.   I have been all over these forums, some other groups, and newegg, and this is what I've compiled for my hardware so far:

Biostar TF560, using onboard audio & network
AMD Athalon 64 X2 4000+ Brisbane 2.1GHz Dual Core
2GB A-Data memory
EVGA 256-P2-N297-LX GeForce 6200LE 
1xWD800JD 80GB for system
3xWD5000AACS in RAID5/LVM for everything else

This is for a master back/frontend, and will also be a file server and a few other things.  Initially, I intend to take the svideo (from card) & analog audio (from MB) out to a modulator for distribution through my existing coax.  Next phase is a dedicated front-end for HD - so this box doesn't need to output in HD.

First question - does that hardware seem to be ok for my purposes?  I'm also toying with the idea of running vmware or something similar so I can have a small windows server on there as well, for some things that aren't linux friendly.  That would mostly be idle though, so not a big processor worry.

Second question - I'm completely confused on how a remote will work.  It will probably make more sense once I have something in front of me to work with, but here's what I think I have figured out - I have an old radioshack 15-1994 with the six-pin thing by the batteries, and I'm pretty excited about re-programming it to do my bidding.  If I use a serial IR receiver (common on ebay) I can then use lirc, right?  Do I need a keyboard for normal operation?  I'm concerned about the WAF here - when she sits down to watch TV, I need the remote to "just work"

Third question - Tuners...  I'm 30 miles south of Chicago, and I intend to only use ATSC OTA.  (This is part of a bigger initiative to ban Comcast from my home, and all Chicago networks are ATSC already - according to antennaweb.org)  I've seen the Avermedia A180, Kworld 115, air2pc, pchdtv 3000, HDHomerun - I'm trying to figure out what my most cost effective option is.  I want 2 tuners minimum, maybe 3 if I can get a good deal (I have 3 open PCI in my proposed mainboard).  I would prefer a card that does hardware encoding to take the strain of my proc.  This is the part that I haven't decided on - any tips/recommendations?

So, am I way off base on my current thinking?  This is my first post into the wonderful world of Mythbuntu - I'm sure it won't be the last.  I'll share the wealth once I figure it out for myself... :)  Thanks in advance!

---

### Post by volkswagner on 2008-04-23
ATSC tuners just grab the already MPEG2 stream.  You will not need nor find hardware/software encoding.  From what I have read performance on these cards are equal to humans.  Choice should be based on Linux support, form factor, price.  Look into multi-record.  This will allow you to record multiple channels with one tuner.

---

### Post by bah1976 on 2008-04-23
Well that's new and interesting information.  Not sure I understand the bit about being equal to humans though...

If I don't need a hardware encoder, that opens up my options quite a bit.  If all I'm doing is capturing the mpeg2 stream, that's pretty sweet.  Does this mean that anything I capture is HD?

So a quick review of multirec says that a tuner can capture any number or streams in a multiplex.  Does anybody have a reference to a US mux listing somewhere online?  I'm trying to determine what "mux" my local stations may be in to plan for the number of tuners I need.  I'm sure the sub channels (NBC, NBC.1, NBC.2, etc) are all in the same mux, but are you suggesting that different networks may share a mux as well?

---

### Post by larsolav on 2008-04-23
> If I don't need a hardware encoder, that opens up my options quite a bit.  If all I'm doing is capturing the mpeg2 stream, that's pretty sweet.  Does this mean that anything I capture is HD?
- Anything you capture with the digital tuners will be in digital format. If the program is in HD it will record in HD, and if the programming is in SD digital it will record SD digital. Over the air lot of stations offer programs in HD. Most blockbuster network prime time shows are HD. 

> So a quick review of multirec says that a tuner can capture any number or streams in a multiplex.  Does anybody have a reference to a US mux listing somewhere online?  I'm trying to determine what "mux" my local stations may be in to plan for the number of tuners I need.  I'm sure the sub channels (NBC, NBC.1, NBC.2, etc) are all in the same mux, but are you suggesting that different networks may share a mux as well?
I think that f.ex. NBC1, NBC2, NBC3 (if your local affiliate offers three program streams) are on one mux. Over the air they all travel over the same frequency (for example the frequency for channel 2). However, the program streams for your local ABC are on a mux on a different frequency(for example the frequency for channel 13). A single tuner can only tune to one frequency at the time, but with myth .21 i think you can now record separate program streams over the same mux at the same time.

---

