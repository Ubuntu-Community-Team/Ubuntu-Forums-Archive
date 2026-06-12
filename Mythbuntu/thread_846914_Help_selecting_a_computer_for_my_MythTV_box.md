---
title: "Help selecting a computer for my MythTV box"
date: 2008-07-02
forum: Mythbuntu
---

### Post by bglaze1 on 2008-07-02
I currently have an old Dell Dimension 8200 which I was upgrading a little to use as my MythTV box.  But my work gave me two partially gutted systems.  One is a Dell Optiplex GX260 and the other is a Dell Precision 340.  

So I was wondering which of these would be the best to upgrade.  Obviously the processor on my Dell Dimension 8200 isn't fast enough to handle HD (a P4 1.3GHz with 1GB RAM), and I am not exactly sure what the other systems have since they don't have RAM currently.  

But someone gave me the impression that you couldn't just upgrade to a 2.4GHz processor on any old motherboard.  So I wanted to check to make sure that I started upgrading a system that would be capable of handling HD, rather than wasting a lot of time and money only to find that I was limited by the motherboard.  So if that is true, how can I tell if my system could handle me upgrading the processor to something that would handle HD?  

And if it does matter which motherboard you have, then which of these three systems would best handle upgrading to a processor capable of handling HD?

Thanks.

---

### Post by mrand on 2008-07-02
> **bglaze1 said:**
> I currently have an old Dell Dimension 8200 which I was upgrading a little to use as my MythTV box.  But my work gave me two partially gutted systems.  One is a Dell Optiplex GX260 and the other is a Dell Precision 340.  

So I was wondering which of these would be the best to upgrade.  Obviously the processor on my Dell Dimension 8200 isn't fast enough to handle HD (a P4 1.3GHz with 1GB RAM), and I am not exactly sure what the other systems have since they don't have RAM currently.  

But someone gave me the impression that you couldn't just upgrade to a 2.4GHz processor on any old motherboard.  So I wanted to check to make sure that I started upgrading a system that would be capable of handling HD, rather than wasting a lot of time and money only to find that I was limited by the motherboard.  So if that is true, how can I tell if my system could handle me upgrading the processor to something that would handle HD?Howdy bglaze1, You may have to do some extensive googling, or maybe search someplace like AnandTech forums to find that answer.
> And if it does matter which motherboard you have, then which of these three systems would best handle upgrading to a processor capable of handling HD?  Thanks.Without hardware acceleration, you'd need one of the very fastest P4's, and actually that is probably not enough for the hardest 1080p H.264 streams.  If you got a Nvidia 5xxx, 6xxx, or 7xxx series video card that provides hardware acceleration, you might stand a chance with a slower P4.  Search  the myth-users mailing list archive - this is a recurring topic (even if I don't know the answer when asked about a P4).  The mythtv wiki may also list "known good" setups.

Good luck,
[INDENT]
   Marc[/INDENT]

---

### Post by nasha on 2008-07-02
I agree with the last poster, you certainly need a high-end stock P4 to run HD... If you have the potential of multiple HD streams your lost.

The gx260 with the addition of a video card will be perfect for a frontend. I use them as frontends for all my installs for their low price, and small form factor.

As for whether you can stick a 2.4ghz CPU into your motherboard, your going to need to locate your motherboard specs to find out whats its compatible with.
> 
Minimum System Requirements:

    * 1.0 GHz x86 or x86_64 Processor
    * 192 MB of system memory (RAM)
    * 2 GB of disk space (Frontend Role)
    * 20 GB of disk space (Backend Role)
    * Graphics card capable of 1024x768 resolution
    * Supported TV Tuner Card (Backend Role)

Recommended System Requirements:

    * 2.0 Ghz x86 or x86_64 Processor*
    * 1024 MB of system memory (RAM)
    * 10 GB disk space (Frontend Role)
    * 80 GB+ disk space (Backend Role)**
    * nVidia 128MB Graphics Card w/ TV-Out or equivalent***
    * Supported TV Tuner Card (Backend Role)

* A 3.0 Ghz processor is recommended for frontend installations using HD video due to the increased load upon decoding. A lower end processor can be used however with multiple functions on a single machine (ie - Frontend/Backend Install) it is not recommended.
From [HTML]http://www.mythbuntu.org/requirements[/HTML]

---

### Post by bglaze1 on 2008-07-02
Thanks for the replies.  
I was wondering though about upgrading my processor.  I was pretty sure that the P4 wouldn't meet my needs, but I wasn't sure if I could upgrade processors on any motherboard or if there were specific processors that only worked on certain motherboards.  
I will definitely have a look at the AnandTech forums.  Thanks for getting me pointed in the right direction.
If anyone had any idea which of these three systems current motherboards would be the best to use with a new processor, I would appreciate it.  I am assuming there is a standard motherboard Dell uses in these systems (the Precision may have a different motherboard than the Optiplex or the Dimension, but I would assume all of the same line have the same motherboard).  So if you know how I can find out which motherboard I have so research this a little better (whether or not it can handle a HD capable processor), I am not sure how to detect this.  Do I need to be able to boot the system to get this information?  Or would there be somewhere to look on the motherboard itself to get the information.  Thanks.

---

### Post by volkswagner on 2008-07-02
Using dell support website and the service tag number should give you specs on the internals.

For processor upgrades some key information is the bus speed.  I am no expert but have had some experience.  Usually the mobo and CPU are rated like 400/533 or 533/800.  The 3Ghz processor is the latest socket 478 rated at 800.

In my past experience mythtv .20 included with mythbuntu 7.10 was more friendly with HD playback on my Dell 4200 running P4 2.4Ghz and Nvidia 6200 AGP 8x card.

Sound can also be an issue with HD recordings since it is multi channel.

---

### Post by newlinux on 2008-07-03
FWIW, I have a P4 2.6Ghz (HT) that plays back HD fine, but not with a lot of other processes running - even without using XvMC and with an old Geforce 440MX graphics card (this is back on .20.2). It also is a 3 tuner slave backend.

---

### Post by mrand on 2008-07-03
> **newlinux said:**
> FWIW, I have a P4 2.6Ghz (HT) that plays back HD fine, but not with a lot of other processes running - even without using XvMC and with an old Geforce 440MX graphics card (this is back on .20.2). It also is a 3 tuner slave backend.Mind describing what HD streams you are able to play back with that setup?  Specifically:

[LIST=1]
[*]How was it compressed (MPEG-2 or 4, H.264, or AVC)?
[*]What bit-rate is the stream?
[*]What resolution is the stream?
[/LIST]

Considering that high bit-rate H.264 streams are difficult to play on 2.6 GHz Core 2 Duo's, so I'd be very leery of spending much money on a P4 setup.

[INDENT]   Marc[/INDENT]

---

### Post by newlinux on 2008-07-03
> **mrand said:**
> Mind describing what HD streams you are able to play back with that setup?  Specifically:

[LIST=1]
[*]How was it compressed (MPEG-2 or 4, H.264, or AVC)?
[*]What bit-rate is the stream?
[*]What resolution is the stream?
[/LIST]

Considering that high bit-rate H.264 streams are difficult to play on 2.6 GHz Core 2 Duo's, so I'd be very leery of spending much money on a P4 setup.

[INDENT]   Marc[/INDENT]


I'm was talking strictly ATSC and QAM  recordings from tuners, so mpeg-2 of course, 720P and 1080i. I can't remember exactly the last time i tried to play anything x264 on my P4, but I do remember some studders when trying, but it was able to with a lightweight window manager if I wasn't doing anything else (720p only). 

That said, I can play 720p x264 on my X2 3800 with a 6200 card without a problem. No Core 2 duo needed. Never tried a 1080p x264 on any of my systems.

I'd be leery of spending money a P4 as well if i were starting from a new system, but if all I want to do is playback mpeg-2 HD recordings from digital tuners and I already had a P4 motherboard and could find a proper P4 on the cheap i would.

---

### Post by DutchLoki on 2008-07-04
> **newlinux said:**
> I'm was talking strictly ATSC and QAM  recordings from tuners, so mpeg-2 of course, 720P and 1080i. I can't remember exactly the last time i tried to play anything x264 on my P4, but I do remember some studders when trying, but it was able to with a lightweight window manager if I wasn't doing anything else (720p only). 

That said, I can play 720p x264 on my X2 3800 with a 6200 card without a problem. No Core 2 duo needed. Never tried a 1080p x264 on any of my systems.

I'd be leery of spending money a P4 as well if i were starting from a new system, but if all I want to do is playback mpeg-2 HD recordings from digital tuners and I already had a P4 motherboard and could find a proper P4 on the cheap i would.


yah H.264 full hd keeps being a problem under Linux/mythTV. My Machine cover really gets hot playing this kind of media. Hope hardware based H.264 decoding comes to linux soon.

---

