---
title: "TV-Card Medion 5044 (SAA7134) - No sound"
date: 2008-08-13
forum: Multimedia Software
---

### Post by skaface on 2008-08-13
Hi,

as mentioned in the thread title, i don't get any sound over my tv-card and xawtv.

I already followed the suggestion from the SAA7134-Wiki from ubuntuusers.de ([this one]("http://wiki.ubuntuusers.de/saa7134?highlight=saa7134")), but that doesn't help me any further (modprobe -v tuner qss=0).

At the beginning there was no sound at all, but since i activated the channel "Analog M" over the "GNOME Alsa Mixer", i get at least a noise, which definitely comes from the line-in, over which the tv-card is connected. I can assure that this noise comes from the line-in and the tv-card because you can hear it, when you switch channels in xawtv...

Is there any info i could supply here, accept that i'm running a pretty fresh installed Ubuntu 8.04?

There is 1 thing left: by use of "dmesg | grep saa7134" i noticed the following lines:

> [52121.257116] saa7134[0]: seems there are two different versions of the MD5044
[52121.257117] saa7134[0]: (with the same ID) out there. If sound doesn't work for
[52121.257118] saa7134[0]: you try the audio_clock_override=0x200000 insmod option.

Unfortunately i don't know what that means and how i could try this ismod option. Any help here?

thanks, regards

mik

---

