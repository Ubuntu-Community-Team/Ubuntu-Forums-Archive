---
title: "Divco card not recognized correctly?"
date: 2008-05-03
forum: Mythbuntu
---

### Post by colinnwn on 2008-05-03
Hi,

I have a Dvico Fusion HDTV 5 Lite video capture card that seems to not be recognized correctly.  

Under Backend Setup>General>Locale Settings>TV format, ATSC is not an option.  I tried NTSC.  Then under Capture Card Setup>DVB DTV capture card (v3.x) it says "could not get card info for card #0 subty...".  I tried Analog V4L and the probed info says "BT878 video **UNKNOWN/GENER..."  With this I only get static.  I'm going for digital OTA first, and analog OTA second.

I've searched around on the internet for several hours tonight and come to dead ends or old info.  _Can anyone advise on how to get this working?_

I'd like to get a HD Homerun or pcHDTV device because people seem to have the least trouble with these.  But unfortunately the Dvico and Kworld products are more my price range.

Thanks.

```
[   23.014142] bttv: driver version 0.9.17 loaded
[   23.014146] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   23.054856] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8996c00 (IRQ: 20), 00:1b:b9:61:ed:03
[   23.054860] eth0: GMII mode.
[   23.054866] eth0: Enabling Auto-negotiation.
[   23.086661] bttv: Bt8xx card found (0).
[   23.086691] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 21
[   23.086703] bttv0: Bt878 (rev 17) at 0000:00:09.0, irq: 21, latency: 64, mmio: 0xcffff000
[   23.086719] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   23.086747] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   23.115766] bttv0: tuner type unset
[   23.115769] bttv0: i2c: checking for MSP34xx @ 0x80... found
[   23.221420] bttv0: i2c: checking for TDA9875 @ 0xb0... found
[   23.558196] tda9875: TDA9875 Rev.0 detected at 0xb0
[   23.667708] tda9875: init
[   23.667864] bttv0: i2c: checking for TDA7432 @ 0x8a... found
[   23.711711] tda7432 0-0045: chip found @ 0x8a (bt878 #0 [sw])
[   23.711844] bttv0: registered device video0
[   23.711864] bttv0: registered device vbi0
[   23.866553] bt878: AUDIO driver version 0.0.0 loaded
[   23.866598] bt878: Bt878 AUDIO function found (0).
[   23.866620] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 16 (level, low) -> IRQ 21
[   23.866626] bt878_probe: card id=[0x0], Unknown card.
[   23.866627] Exiting..
[   23.866631] ACPI: PCI interrupt for device 0000:00:09.1 disabled
[   23.866637] bt878: probe of 0000:00:09.1 failed with error -22
```

---

### Post by cybersapient on 2008-05-07
Hmm... I'm having the same error message with a PCHDTV 3000 card. I see no mention of it in the forums- I'm wondering why I'm "special"...

I have a P4 2.4 GHz machine, 512 MB ram, 500 GB HDD, Generic NVidia 7300 GT card, and MYTHBUNTU 8.04 distribution (installed fresh from downloaded CD).

I had the card working prior to installation of this version- now the card is not being recognized. Perhaps I am missing some critical driver, but I am clueless as to where to start to determine what driver that might be.

Any assistance would be greatly appreciated. 


Regards,

Shane

---

### Post by colinnwn on 2008-05-07
I haven't resolved it yet, but I am in the middle of researching the options.  I have half the resources I was looking at bookmarked here and I will try to do the rest tonight.

[http://del.icio.us/colinnwn/mythbuntu-troubleshoot](http://del.icio.us/colinnwn/mythbuntu-troubleshoot)

---

### Post by cybersapient on 2008-05-27
Hi Colinnwn,

Have you had any luck? I am just getting back to trying to make my MythTV box work.  I am trying to decide what I should do- try to get the dvb driver loaded so my PCHDTV card works, or go back to MythBuntu 7.something, and upgrade...

The reason I decided to try 8.04 is because the 7.10 version had a "stuttering" problem on recorded, as well as played-back HD material. 480P would play back well, 720p would cause occasional stutters, and 1080i seems to have stutters about once every few seconds...

Thanks for your reply. Perhaps we will get this working soon!!

Shane

---

### Post by colinnwn on 2008-05-28
I did get the Dvico card working and I wish I could tell you what did it.  Everything I tried is in the link above, but nothing seemed to work.  

When I was working on the analog feature of this card, someone in another thread said for digital I should set it up as DVB card and scan for channels.  I previously set it up as DVB when it wasn't recognized, but I didn't scan for channels because in analog that messes up your schedules direct channel mapping.  I thought what the heck I'll try again, and sure enough when I switched from V4L to DVB all of a sudden the card was recognized. 

Strangely I can no longer get an analog picture out of the Dvico card when I set it up as a second V4L capture device.  And the recordings I made in analog will no longer play back correctly in full screen, but they do play normally in the "Watch Recordings" preview screen. 

With new digital recordings, I now get very consistent studdering, it plays normal for 1 second, stops for just under a second, plays normal for 1 second, and on.  Every once in a while a recording will play back normally.  In the backend logs I have "NVP prebuffering pause".  I have searched for a fix and found no conclusive answers or solutions.  My last attempt was PCI latency but that made no difference.  I haven't identified if the resolution makes a difference because I don't know how to view a recording's resolution.

I'll post here and add the link to my del.icio.us bookmarks if I have any further success.

---

