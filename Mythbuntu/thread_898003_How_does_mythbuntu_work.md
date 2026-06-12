---
title: "How does mythbuntu work?"
date: 2008-08-22
forum: Mythbuntu
---

### Post by acrousey on 2008-08-22
I guess I'm not as up to date with technology as I thought I was. How does mythbuntu work? Would I be able to watch TV or even download TV shows to my computer? Is this a free service or is there a subscription fee? I'm sorry if I sound like a noob in all this.

---

### Post by nickrout on 2008-08-22
It is a media centre. You can watch and record tv, watch downloaded or DVD movies, plus a lot of other stuff.

[http://mythtv.org/modules.php?name=MythFeatures](http://mythtv.org/modules.php?name=MythFeatures)

---

### Post by acrousey on 2008-08-25
One thing that I have been trying to figure out is if it is actually a free service or not. When I was looking around the MythTV website, I saw something about a subscription Schedules Direct. What would that have been about? Sorry if it sounds like I'm asking dumb questions, but sometimes it's better to get it out of the way right away than look stupid later on.

---

### Post by eldragon on 2008-08-25
you are not getting how it actually works.

it does not download anything from internet. you need a tv capture card for it to work correctly. after that, it requires hours of config and tweaking to get it working correctly.

id recommend a dedicated computer for the task, it doesnt need a monitor since the backend runs as a daemon. then you can connect with the client through your regular computer / notebook. you will only need the capturing harware for the server/backend. clients / frontends stream the data through the server :D

hope i cleared some stuff up.

good luck

---

### Post by raul_ on 2008-08-25
And yes it's free. The subscription service should be to download shows's information, so you can see what it's on right now, what's up next, what's up tomorrow, things like that. But you can do that for free.

---

### Post by acrousey on 2008-08-25
@eldragon
> **eldragon said:**
> 

id recommend a dedicated computer for the task, it doesnt need a monitor since the backend runs as a daemon. then you can connect with the client through your regular computer / notebook. you will only need the capturing harware for the server/backend. clients / frontends stream the data through the server :D

hope i cleared some stuff up.

good luck

And the dedicated machine would have Mythbuntu on it? Would I be able to stream it to another computer?

---

### Post by raul_ on 2008-08-25
> **acrousey said:**
> @eldragon


And the dedicated machine would have Mythbuntu on it? Would I be able to stream it to another computer?

Yes, but you could also watch it in the computer that hosts the backend

---

### Post by acrousey on 2008-08-25
Alright, thanks guys. I don't think I'll be able to do it now or anytime soon, seeing as how I'm a poor college student, but I think it could be a fun project next summer setting up a computer for this.

Do you think an old Compaq Presario manufactured in or around 2000 would be able to support a TV card and/or a graphics/video card other than the integrated one?

---

### Post by nickrout on 2008-08-25
> Compaq Presario 5127SR, Pentium 3 Processor, 512MB RAM, 40GB + 750GB Hard Drive, Integrated Graphics Card, Original OS: Windows ME, Current OS: Ubuntu 8.04

If this is the machine, it will be borderline for SD material and definitely will not work for HD material. You don't actually say the speed of the processor, or the chipset of the video card, and these will make a big difference.

Specs of the machine are here by the look of it. [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00009391&lc=en&cc=us&dlc=en&product=93076&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00009391&lc=en&cc=us&dlc=en&product=93076&lang=en)

Processor (1GHz) is probably enough for a basic SD machine if you are using a hardware video encoder like a PVR 150, but the specs still do not specify the video chipset. 

> lspci 

will give you the chipset of your video.

---

### Post by eldragon on 2008-08-25
i was suggesting a standalone server for the backend since it must stay on in order to work as a personal video recorder. scheduling programs at insane hours, or during work time / class time. or even transcoding to a more compressed format during the nights.

1 computer alone should be enough to include the frontend / backend for mythtv. (the program behind mythbuntu). you will have to leave it on 24/7 if you wish to take full advantage of mythtv.

---

### Post by Nate B. on 2008-08-25
If you're familiar with the likes of a Tivo or other Digital Video Recorder, then you'll understand the main thrust of MythTV.  But MythTV is much more than that.  Some things I'm aware of that it can do is host a music collection, stream Internet "radio", store photos, archive DVDs, and probably more that I'm not aware of.  Best of all, it's built on the Internet's Free OS, Linux.  While the software is free for you to install and use, the tradeoff is that you'll invest some time learning and understanding MythTV (if you're new to a UNIX type system, then some learning may be necessary for it as well) and spend hours tinkering and learning.

For SDTV (from an S-Video or composite connector on a set top box), a relatively modest system can serve quite well.  I built my system from a second hand Thinkcentre off of ebay, a new PVR-150, used Soundblaster Live! card, new Western Digital 1TiB drive and a new DVD+R/RW drive.  The drives just about doubled my "investment".  I would have gone with an AMD system I already had but learned that the PVR-150 has DMA issues with the Via chipset, so I went with Intel.

Sure, I spent more than just going with a DirecTV provided DVR, but this is way more fun and capable.

BTW, the Schedules Direct subscription is modest at $20/year and provides MythTV with a "TV Guide" that is used to schedule recordings in a much more capable manner than that used by the typical VCR.

---

### Post by acrousey on 2008-08-26
This is what I get when I do "lspci""
```
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
01:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
01:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

```

I think it's the integrated graphics/video card. But do you guys think it will still work as a substitute TiVo?

---

### Post by Nate B. on 2008-08-26
Unless you plan to use a VGA to S-Video or composite video like an Averkey product, or you have a TV that takes VGA input, you'll want some sort of TV video output.  I am now using the integrated i865G graphics on my Thinkcentre with an Averkey iMicro and the result is better that with the FX5200 I had tried.  My TV wouldn't work with S-Video output using one of those adapter cables so I had gone the Averkey route using the card's VGA output.

I'd say it's worth a try and will probably work if you can watch a DVD full screen on it.

If there is a downside to the Averkey it is that the units I tried both seem to gradiate the color and I see interesting shading of hues.  It's most pronounced on flesh (faces and such) and turf and pavement that normally have subtle shading which the Averkey tends to pixelize into larger blocks.

---

### Post by acrousey on 2008-08-26
Maybe I'll try to turn this computer into it. My room mate said he'd "pitch in for the cause". What kind of hardware should I be looking into? A TV tuner? Would I want to get a video card to watch the shows on TV? And would this new hardware require me to get a new power source (the current one is 115V)?

Again sorry for all the questions. I'm just scared that my comp might not be able to handle all this.

---

