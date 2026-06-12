---
title: "Audiohardware, Soundcard, low latency, at least 4xIn 4xOut"
date: 2007-05-18
forum: Multimedia Production
---

### Post by Daniel_D on 2007-05-18
Hi all,

im quite new to audioprocesing under linux - but i have already done some audiostuff (the analog way). Now i would like to use a PC as an advanced realtime audio-(post-)processor at live speeches.

I worked as an technican (setting up) and also as audio-jocky for conferences (this means live speech, and audio from various sources) for some times.

For the next time, i plan to use UbuntuStudio on a PC to do some frequenzy-filtering and other cool stuff. Here now some questions:

The PC is not bought yet - what components should i care for?
[INDENT](planned: ~2Ghz DualCore Intel, 2GbRam, 2SATAs in LVM striped, dualscreen) [/INDENT]
and SOUNDCARD? Is there any soundcard someone would recommend, or does every bit better card work for these things. How much latency should i expect? And what can i do, to keep it as low as possible?

How much latency is acceptable at all (at live conferences)?

Does anybody know a good feedback-canceler (for linux, jack of course)?

Thats all (quite a bit, thu?) for now, thx for all answeres!

TIA
Daniel

---

### Post by OoooMatron on 2007-05-18
I just installed US and it works great my with terratec 24/96 PCI sound cards. its a 24 bit sound card with low latency and works without any noticeable effect delay at 256. Card seems to work as low as 128 and I haven't tried to put it any lower. I would say both these settings are suitable for live work.

most pro end cards from a few years back seem to work but you can check at the alsa page which cards are supported out the box.

can't answer your other qs.

---

### Post by theorganloft on 2007-05-18
You don't need much to have a great recording system.  I built a system with a Sempron 3000, PCHIPS 754 socket MOBO with Network, Graphics and Sound and added a Sounblaster Live PCI card.  I put 512 Mb of memory, a 250 gig SATA drive with an extra cooling fan on the drive. I added a DVD writer.  This system cost me $300.00. The monitor is a 19inch LCD.

I used Mepis 6.5 then loaded Audacity.  You can also use Umbuntu Studio and get great results.  If you want to edit video, add a PCI express graphics card and add 1.5 gig. I would also add a second 250gb or larger HDD.

Buy good audio cables. I like the Monster cables that are designed to be used on the IPODS.

---

### Post by jondecker76 on 2007-05-18
For sound card, I would recommend an MAudio Delta series (I have a 1010, but they also make a 44 and a 66). I've never had a bad experience with it, and for the most part have heard great reviews from others using Delta series cards.

With my very modest setup, using the Ubuntu Studio Low Latenency kernel, I have no problems running below 3ms, and could probably do even better than that with a little tinkering.

I would think that anything under 5ms should work fine for a live conference, possibly even up to 10ms, but of course, the lower the better

---

### Post by kayosiii on 2007-05-24
The 1010 is well regarded... I personally use a presonus firebox which I am quite happy with.

Its probably worth joining the linux audio users mailing list.

---

### Post by Daniel_D on 2007-05-25
Hello!

Thx for the numerous feedbacks... I guess the choice will go to "M-Audio Delta 1010 LT" or the "M-Audio Delta Audiophile 2496" looks also promising, if i can life with 2xI/O.

So - thx so far... are there any suggestion for feedback-canceling (realtime, jack).

I have looked so far at jamin - looks very cool. And at least for manual canceling (via eleminating feedback frequenzies) it would be very usefull. But ther should also be other solution than eleminating frequenzy-bands (which may have hearable negative effects on speech/sound-quality). Like frequenzyshifting and other stuff...

Any experiences?

Thx so far,
Daniel

---

### Post by tgalati4 on 2007-05-25
I've used donated components for church recordings:  PII 300 MHz, Delta M-Audio 66 card (sweet), Dynebolic 2.2 (2.4.2 is out now).  You don't need to spend a lot to get decent recordings.  For feedback control, I've used Sabine units for professional gigs.  They make a slick on-mic-stand DSP "microphone rider" for about $150.

Check craigslist.org for some deals on used audio equipment.  I live in LA so I'm kind of spoiled by the daily dump of equipment from the studios.

---

### Post by kayosiii on 2007-05-25
Off the top of my head I would say try a parametric EQ plugin or a notch filter and make the band very narrow. Of course I might just be exposing my ignorance there.

---

### Post by sgx on 2007-05-26
You might install ladspa and  ecamegapedal, which hosts ladspa plugins, and look for compressor/limiter/eq 
type plugins from the ladspa collection, then simply test and choose plugins, and route your audio output to the ecamegapedal input...and connect ecamegapedal output to  alsa_pcm input...hope this helps...
mAudio 24/96 works fine here...

---

