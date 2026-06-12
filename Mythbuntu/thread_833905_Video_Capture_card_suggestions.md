---
title: "Video Capture card suggestions?"
date: 2008-06-19
forum: Mythbuntu
---

### Post by bglaze1 on 2008-06-19
I am trying to upgrade my computer to use as my Myth TV box.  I currently have a P4 1.3GHz processor, 1GB of RAM, and a NVidia FX 5200 graphics card.  I am trying to decide which capture card to get.  

I was thinking about getting the Hauppauge PVR-500 but then I realized that it wouldn't work after the digital switchover next year (at least the way I understand it.  Is that correct?).  So I am trying to decide which digital tuner card to get.  

I want something that works well with Myth TV.  I want to be able to record two channels at once.  I also want to be able to record over the air digital, even if it isn't fully HD.  I currently just receive an analog signal from an antenna in my attic.  But I would like (if possible) a card that would upgrade well with either cable or satellite.  And have the ability to do full HD in the future.  

What would be a good tuner that would fit these requirements?  

Thanks for you help.

(I also found an AMD Athlon 64 X2 4800+ Brisbane 2.5GHz 2 x 512KB L2 Cache Socket AM2 65W Dual-Core Processor on NewEgg.com that I was considering purchasing if that would help in going to full HD.  Any thoughts?)

Thanks again.

---

### Post by Cresho on 2008-06-19
I have an old avermedia for analog and I have expirience with KWorld_ATSC_115 which is perfect on my system running me-tv. (research for myth but I believe it is supported) [http://mythtv.org/wiki/index.php/Kworld_ATSC_110](http://mythtv.org/wiki/index.php/Kworld_ATSC_110)  Here is a avermedia high definition tuner tutorial version.[http://ubuntuforums.org/showthread.php?t=715165&highlight=avermedia](http://ubuntuforums.org/showthread.php?t=715165&highlight=avermedia)

a small tutorial on install using kworld 115 [http://ubuntuforums.org/showthread.php?t=734867&highlight=hdtv](http://ubuntuforums.org/showthread.php?t=734867&highlight=hdtv) using me-tv but it also shows you how I got the hardware working.  If you are fancy enough, you can get 2 of these cards and run 2 different windows like I have but i use an analog and an HDTV card.  Currently working on the HVR1600 (not supported).

The tutorial in mythtv is dated but if you use mines, (ubpdated), all you need is ubuntu to have the hardware working and when you install myth tv, it's all about configuring it.  With me-tv, you can run high definition and record like nothing(just need a good antenaHD).

---

### Post by bglaze1 on 2008-06-19
Thanks for the reply, Cresho.  
Does the AverMedia card support digital recordings?
The KWorld 115 says it has support for both analog and digital.  Do you know if it is possible to record dual digital cahnnels with this card, or does it only allow one digital recording and one analog recording?  Because if that is the case then it won't be a dual tuner next year.  Other than that, it looks like a great fit. 

My big concern is that I want to have dual channel recording capability, but I don't want to have to purchase a new card in less than a year because the analog tuner will be worthless.

Do you  have suggestions that would be capable of handling dual digital recordings?

---

### Post by volkswagner on 2008-06-19
If you are using CATV check with your provider.  Most cable companies will still send analog.   The k-world 110/115 does not have a hardware encoder.  Your system will be under powered to playback digital recordings if they are broadcast in HD.

---

### Post by bglaze1 on 2008-06-19
So that brings up a couple of questions:
First, I am currently receiving analog signals through an antenna in my attic, so I would be migrating to over the air digital signals.  And I am a little confused, I thought that if I were receiving over the air digital signals that I wouldn't need an encoder because I would just be capturing data and storing it to disk, no conversion necessary. Is that correct?

If that is the case, I would prefer to just capture two digital streams at the same time and not need to do any processing on the streams.  Do I just need to get two tuner cards, or is there a card that has the ability to capture dual digital streams?

Volkswagner said that my system would be underpowered to playback digital recordings in HD.  Does that mean with the KWorld 115 I would be underpowered to playback HD?  If that is the case, what would be a good card to capture HD content?

Or does that mean my system currently wouldn't be able to handle HD regardless of what tuner I get?  
If that is the case, would upgrading the processor I listed earlier help?

Thanks in advance for all your help.

---

### Post by Cresho on 2008-06-20
Your current pc cannot handle HD as I am aware you probably need lightning fast cpu and i was using a 3200xp amd at the time with 1gb memory.  when i view analog and digital on my pc with amarok running in the backround and compiz fusion, i get around 21% cpu usage.  when both cards are recording at the same time (one analog and other digital), i get around 60 percent cpu usage as I am typing this while listening to amarok and compiz on.  Yes you do need a more powerfull cpu, DDR800 Memory at least.

2 digital cards and recording?  hmmm never tried this because my third digital card is not supported.

current hardware 
black edition x2 amd 6400
ddr800 2gb
gigabyte motheboard.
bfg 8800gt graphics card.

sata 300 drives.

I updated my pc just because I had small issues with my old setup regarding memory, hardrive and hdtv.  It was slow accessing channels and it gaved my pc a workout.

---

### Post by DutchLoki on 2008-06-20
the Hauppage WinTV-HVR-2200 seems a nice choice for its dual tuner setup. I use a different card for my mythbox so you need to check out the current support I advise you the following for any card you choose: 

[http://www.mythtv.org/wiki/index.php/Tuner_Card#Cards_tested_with_MythTV](http://www.mythtv.org/wiki/index.php/Tuner_Card#Cards_tested_with_MythTV)

[www.linuxTV.org](www.linuxTV.org) (contains a list of supported cards)

[http://marc.info/?l=linux-dvb&r=1&w=2](http://marc.info/?l=linux-dvb&r=1&w=2) (do a search on this mailing list for recent changes etc.)

---

### Post by bah1976 on 2008-06-20
In no particular order, here are my random thoughts:

In my area (30 miles south of the Sears tower in chicago) all stations are already broadcasting digital, aka ATSC.  Rather than build a system that would be outdated in a year, I just built my first myth box to capture the ATSC signals and I don't even bother capturing any analog (NTSC).  I have two kworld 115 tuners in my box, with the antenna split between them.  That gives me two tuners for a pretty low cost.  I got mine on ebay for about 40 w/shipping - newegg had them recently for 50 with free shipping.

With the kworld 115, there are two coax inputs - I have the top connected to the antenna and the bottom connected to my comcast feed.  In this way, I'm able to tune unencrypted QAM256 channels as well.  It's still just a dual-tuner setup - the 115 card cannot tune a signal from both inputs at the same time.  But I can do 2xATSC, 1xATSC & 1xQAM256, or 2xQAM256.  If this is just a backend, the incoming video stream is just captured and written to the disk unmodified (as you suspected) - so not a lot of horsepower is needed for that part, even if you're recording HD OTA - it just writes the raw data to the disk.  The side affect of this is that you need a lot of disk - OTA HD is about 8GB/hour.

To clarify, recording and playback of HD are two different entities - backend recording OTA HD does not require a lot of processor, but front-end displaying of that video does.  If you're combining frontend/backend, then you will need a bigger proc.  If you're able to build a new frontend to display, and use what you've got to record, you might be ok.

If you want a single device that will tune two channels, google hdhomerun.  That network-based device is ~$170, so compare that with the cost of two single PCI tuners.

One other thought on your antenna - an antenna is not inherently analog or digital - it's all about what's on the other end of the antenna.  In other words, if you plug your antenna feed into an ATSC tuner, you may find that you're picking up digital signals without changing anything in the attic. 

One other thing - the IR receiver included with the kworld does not work without some kernel modification that I wasn't comfortable with - so if you go that route plan for a different remote solution.  The microsoft mce usb ir receiver works pretty easily out of the box.

---

### Post by bah1976 on 2008-06-21
Adding another thought - 
I just noticed that newegg has the kworld 115 for $35 with free shipping!  At that price, buy two and a spare!

---

### Post by bglaze1 on 2008-06-26
Thanks bah1976! That was just what I was trying to find out.  So it appears that if I want to do two digital streams at the same time, I need to get two PCI cards (or the HD Homerun).  The KWorld seems like a great option, considering my budget constraints.  Considering that this would be a combined frontend/backend, it appears I now need to research beefing up the processor.  Any quick thoughts on what would be good enough of an increase?  I have a P4 with 1GB RAM.
It seems my antenna setup should be good for receivin ATSC.  Thanks again.

---

### Post by bah1976 on 2008-06-26
Just to clarify - the existing antenna MAY work.  It also might not.  Digital signals are a little pickier than analog signals, and depending on how many layers of shingles + how far to the tower - you may still have difficulty.  Just wanted to point that out.

As far as a CPU goes - a P4 what?  I have an AMD 4400+, which is a dual core 2.3Ghz processor.  With this proc, I can record 2 shows and watch a prerecorded show.  I don't currently have a HDTV, so I'm not displaying HD, but I'm pretty sure that it doesn't matter, since the stuff I watch is usually recorded in HD, and therefore has to decode it anyway.  For an official word, check here, if you haven't already:
[http://www.mythtv.org/wiki/index.php/Hardware_Requirements]("http://www.mythtv.org/wiki/index.php/Hardware_Requirements")

1GB ram should be fine.  I have 2GB because the 2G kit made sense for my motherboard.  I'm running a vmware-based WindowsXP virtual machine, and I'm still only using 540MB.

---

### Post by bglaze1 on 2008-06-26
Sorry, I don't know how I left that off.  It is a P4 1.3 GHz processor.  I have 1 GB of RAM. And I don't know if this is possible or not, but I would like to be able to display it in HD in the future, but for now a decent standard definition output would be good.  I don't have an HD TV currently so I am not sure how that would work either.  My understanding was that the card would just capture the ATSC stream in HD.

Would I need to do some encoding/decoding on the video to convert the ATSC stream?  It sounded like you mentioned doing this.

And would this require a bigger processor, or could I use what I currently have until I buy the new HDTV and want to display actual HD video?

Thanks.

---

### Post by bah1976 on 2008-06-27
If you're recording OTA ATSC, it's just capturing the mpeg2 frames and writing them to disk.  There is no encoding done when recording.

When you watch this recorded ATSC video, it is decoding the HD/digital signal - regardless of if you have an HDTV.  The video has to be decoded to display it even if you're watching on an old TV.  The video display card will output the decoded signal in whatever quality connector you have - I'm using svideo on a evga/nvidia 6200LE I got from newegg for about $30.  The card also has a DVI output, so when I upgrade to a HDTV, I'll just use that connector and be all set.  

As far as the CPU goes, I think it's a little underpowered for a front-end.  It might just make it, but it could be choppy and highly utilized.  I'd recommend a faster one.  Stick with a faster P4 if you want to keep your motherboard - but my preference is AMD - seems to be cheaper and just as good in my opinion.

---

### Post by simonlesorcier on 2008-06-29
PVR-500 by Hauppauge
2 tuners
1 RCA capture INPUT.
works like a charm.

cheers

Eduardo

---

### Post by DutchLoki on 2008-06-29
There is a special thread about hardware setups: 

[http://ubuntuforums.org/showthread.php?t=566529](http://ubuntuforums.org/showthread.php?t=566529)

Maybe you can take a look there for more ideas.

---

