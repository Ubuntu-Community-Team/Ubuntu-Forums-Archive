---
title: "Artefacting with HVR-1600"
date: 2009-05-12
forum: Mythbuntu
---

### Post by kickinthethroat on 2009-05-12
I am very new to mythbuntu (and linux in general), but I've managed to set it up well.  The only problem I have is video quality.

When i first installed, the video quality was very poor, i played around with the playback settings and interlacers... which is when I installed VDPAU.  I got SD looking 'fairly' decent (it is watchable, though it looks like I'm watching it through a fog), however HD has severe artefacts and jerkiness, and is quite unwatchable.

When I use the standard decoder, the jerkiness and artefacts are still there, however CPU usage goes up.  The only difference VDPAU seems to make, is the CPU usage goes down to about 20-30%, however arefacts and jerkiness remain.

Also, it is not an audio sync issue, since I disabled the audio, and the problem remained.

I can post logs if need be, the only one that stuck out to me are frame CRC mismatches.  Any ideas on how to smoothen the playback?  Thanks for the help.

Specs:

AMD64 X2 Dual 4600+
2gb ram
Geforce 8800 GT

---

### Post by epi 1:10,000 on 2009-05-12
I get more artifacts on my HVR-1600 digital tunner than my HVR-1250 also.  Ina addition the HVR-1600 needs a stronger signal.  I would really like to know if anyone found a fix for this

---

### Post by kickinthethroat on 2009-05-12
Good to know at least someone else is having the same problem.  I currently have it on vdpau and Bob2x with backup temporal 1x.  Seems to cut down on the problems, but they are still there no doubt.

I'm thinking about just buying a pcHDTV 5500 and use that... would that solve my quality problems?

---

### Post by kickinthethroat on 2009-05-13
bump, anyone?

---

### Post by klc5555 on 2009-05-13
> **kickinthethroat said:**
> bump, anyone?

The 5500 will work, and will receive digital better than the 1600. On modern kernels > 2.6.25 (as in 8.10 or 9.04), the analog tuner component of the 5500  will also work pretty well. The 5500 is very easy to set up also, and starts up smoothly at bootup. But it's quite pricey for what it is.

The Phillips tuner cards, like the AverMedia A180 and others, will also work better than the 1600 (lots of cards do digital better than the 1600), and are much less expensive than the 5500, but tend to be tricky to set up for the first time until you get the hang of it. Plus, they can sometimes be a bit stubborn about starting up except after a cold boot.

---

### Post by kickinthethroat on 2009-05-14
Thanks for the input. I was thinking the exact same thing, the 5500 seems to be way too expensive for what it is imo. Looks like the A180 only does HD though... I would ideally like both better analog and digital quality.

---

### Post by klc5555 on 2009-05-14
> **kickinthethroat said:**
> Thanks for the input. I was thinking the exact same thing, the 5500 seems to be way too expensive for what it is imo. Looks like the A180 only does HD though... I would ideally like both better analog and digital quality.

The A180 does both HD and SD digital. There are other not-particularly-expensive Phillips tuner cards that have both analog and digital capabilities.

On the other hand, there's nothing that much wrong with the _Analog_ side of the Hauppauge 1600 --it's only the digital half of the card that's cursed. I continue to use one as an analog-only card, and its recordings, except for channels in the channel 70-99 range (analog cable) where it begins to suffer from signal-strength issues, are of generally higher quality than those of an old Haupauge PVR150 that I still use. 

If you have a PCI (or PCI-e) slot to spare, you may wish to keep the 1600 in-service as analog-only, and supplement it with some cheap Phillips tuner card like the AverMedia A180 for digital coverage (SD and HD). That's the way I have one of my secondary backend machines set up.

Cheers! :)

---

### Post by kickinthethroat on 2009-05-15
Digital with the 1600 is definately cursed, but the analog also looks bad to my eyes, definately worse than it looked in windows.  Its like im looking at it through a fog, i can see like...a little flicker all over the screen. Kind of fuzzy...

Anyway, i went ahead and bought a 5500. It will be easy to set up sure, but I hope the quality goes up a lot

Edit: Ahhhh I feel so dumb!  I had the screen size in the recording profile on 480x480.  I remember i switched it to 720x480 before, but it didn't look right...I don't know what I was thinking.  Analog looks much better now...oh well, I'll still use the 5500 for HD, and then just have 2 analog recorders :)

---

