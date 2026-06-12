---
title: "New to Myth, Ubuntu, PVRs; Planning Stage Questions"
date: 2008-09-26
forum: Mythbuntu
---

### Post by HeavyArms on 2008-09-26
Hello all,

These forums as well as many many other places all have a wealth of knowledge.  Sometimes, that's not always a good thing as I head is completely swimming with conflicting data.

First, I'm a developer, but I've never done much in *nix aside from traverse directories and FTP, mostly Oracle stuff.  So, I'll call myself a n00b for now.  :)

My goal is to make more of a DVR than an HTPC.  I just want to be able to record and play back tv (fancy VCR replacement) and also record network NBC/CBS HD.  Blu-Ray would be nice, but not a must have.  I've read some boards where people claim to have it running, others claim BD on Linux is an uphill battle.

Here, the system requirements seem reasonable, but while investigating Media Center, it seems everyone recomments $1500 Quad Core super computers.  That is only relevant in that I was hoping to use MCE as a fallback if I run into migranes with MythUbuntu.  ... Catch 22 is that from what I've read, newest hardware isn't exactly a breeze with Linux.

Ok, here is what I've picked out thus far, mostly based on price.  I would greatly appreciated any opinions and feedback on my choices thus far (this list definitely isn't set in stone).

CPU - AMD Athlon 64 X2 5200+ 2.7GHz
MOBO - ASUS M3N78-VM AM2+/AM2 NVIDIA GeForce 8200 HDMI Micro ATX
HDD - WD Caviar 500GB 16MB Cache SATA 3GB/s 5400-7200 RPM
TUNER - WIN-TV HVR 1800 Kit
RAM - G.Skill 2x1GB DDR2 1066 Dual Channel
Case/PSU - undecided

Now two targeted questions:
1.  I have basic cable (Comcast) with HD on local networks.  Can I get the HD over the coax?  Is SD over Comcast considered digital or analog?  The tuner says it has 2 tuners built into 1 card, is that an issue?

2.  I've read that Intel chip to Intel Mobo boasts the best video and audio processing.  Anyone care to weigh in on that?

I really do apologize for the wall-o-text.  I'm trying to plan it right in the hopes of a smooth install and I can just enjoy TV instead of beating my head on my desk.

Thank you for the community, your help and your time.

- Heavy Arms -

---

### Post by Caps18 on 2008-09-26
I can't help you too much, but I would recommend a bigger hard drive.  I filled up a 750GB one in 7 months (I could get rid of some stuff, but need some time to watch it.  I'll have more time this winter).  I just added a 1TB drive to store downloaded and backed up TV shows and DVDs on to free up 250GB.

Then again, my Dad has at most 3 shows on his TiVo because he is diligent at deleting stuff and not recording extra stuff.

I'm not sure a 64-bit CPU will be needed for Mythbuntu, but I'm not the one to ask.  I'm running a 1.8 Ghz AMD that cost $30 on eBay.

I will say that you will face some difficulties somewhere along the way, but once it is working, it is the best thing out there.

(I may also recommend the tuner that I have pcHDTV 5500.  It is only for over the air stations, but they are in digital 100%, and HD most of the time now.  It would be a good second tuner since at least two or three times a week I find myself recording two things at the same time.)

---

### Post by DemonBob on 2008-09-26
> **HeavyArms said:**
> Hello all,

...
TUNER - WIN-TV HVR 1800 Kit
...
- Heavy Arms -


The HVR-1800 Analouge support for this card in linux is not working at the momment, although the digtial side of this card from what i hear works rather well. 

I have extended basic cable with charter and bought this card to be a second card beside my PVR-150, but i've been unable to get it to work.

I would recommend going with a different card at the moment.

---

### Post by HeavyArms on 2008-09-27
I appreciate the responses guys.  I'd still like to get some more input from the community as I continue my research.  Keep 'em coming.

- HeavyArms -

---

### Post by newlinux on 2008-09-27
SD over comcast can be analog or digital. SD is the display format, analog or digital is how it transmitted and tuned. In my area comcast sends man analog SD stations, and few SD digital stations (of which many are duplicates of the analog SD stations). All HD stations are digital only. In most areas comcast transmits local HD stations over coax via unencrypted QAM, but it is not guaranteed. I get mine over unencrypted QAM.

The pchdtv 5500 is not only for OTA. IT can tune digital QAM, OTA ATSC, and analog (NTSC - both OTA and cable).

Since HVR-1800 analog support is lacking, I'd recommend a second card analog card like the pvr-150 or a hybrid analog/digital like the pchdtv 5500 or kworld atsc 110/115 or dvico fusion 5s or any number of other older cards.

In general intel chips do a little better at video processing, IMHO, but the X2 5200 you are looking at is way more than enough for processing mpeg-2 HD recordings.

---

### Post by kpatz on 2008-09-27
That system should be plenty powerful enough.  I'm running a Myth box that I built almost 2 years ago, with a Core 2 Duo 6600, and it basically coasts even when recording and watching HD.  I have it running SETI@Home and streaming music using the mpd daemon to our whole-house audio using a 2nd sound card.

Windows, especially Vista is a much bigger resource hog than Mythbuntu.  You won't need a $1500 mega-system to run MythTV.  Any dual-core CPU plus a decent video card (I have an nVidia 7600GT card) will do fine.

I use the pcHDTV 5500 with Comcast cable.  I can get all the analog channels and unencrypted digital channels including HD.  About the only channels that are unencrypted are the basic network channels, but if you only have basic cable that's what you have anyway.

I originally had Ubuntu Edgy 32-bit and MythTV on it, but I recently did a reinstall and put 64-bit Mythbuntu 8.04.1 on.  It works great.

The amount of HD space you need depends on how much recording you plan on doing and how many recordings you want to keep at a time.  HDTV can eat upwards of 7 GB/hour, so take that into consideration.  My box has 1 GB RAM and that's plenty for a Myth box, but RAM is cheap so there's no harm in going with 2 GB.

BTW, why are you going with an Athlon 64 X2?  Those are so last year, AMD has the Phenom chips now.  Unless you're looking to save some $.

---

### Post by HeavyArms on 2008-09-28
Wow, that's some really good info guys, thanks!

Now, If I were to use the HVR-1800 for digital and another such as the pcHDTV5500 for analog, I'm curious to know how MythTV would know which tuner to use to record the show.

Is it like Primary/Secondary on whether the primary gets signal or not, it will switch to secondary if necessary ... or is it like assigning specific channels to specific tuners?

Keep the suggestions, anecdotes and help coming, I appreciate all of it.

- Heavy Arms -

---

### Post by DemonBob on 2008-09-28
It will do both, 

You can assign specific channels to each card, and when you schedule a recording it will pick the apportiate card.

---

