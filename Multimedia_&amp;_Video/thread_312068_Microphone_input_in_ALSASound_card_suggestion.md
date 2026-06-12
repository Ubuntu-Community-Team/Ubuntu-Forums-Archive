---
title: "Microphone input in ALSA/Sound card suggestion"
date: 2006-12-03
forum: Multimedia &amp; Video
---

### Post by robinl on 2006-12-03
I have been messing with TeamSpeak again lately and I just discovered that my microphone doesn't work at all in ALSA. If I aoss TeamSpeak I will get microphone muted which basically mean I don't have microphone input, wine doesn't recognise any input in ALSA and while I can hear myself from the microphone if I un-mute it sound recorder just crashes when I start to record. Running TeamSpeak as itself (ie. in OSS mode) is fine except it takes up the whole sound card to itself.

I have an onboard Realtek ALC850 but it shows up as Nvidia CK8S in sound preferences and I have two seperate devices in Volume Control: CK8S for ALSA and ALC850 for OSS, even there's only one onboard sound card (I think) on my NForce3 Motherboard. 

If it really is unsolvable what would be a good sound card for Alsa? One with hardware acceleration and mixing? I'm thinking about an Audigy2 Value or something but I don't really know about sound card since it was in the 90's when I last touched one.

EDIT: In audacity when I record I get this high pitched sound along with my microphone input.

---

### Post by popacsek on 2007-05-21
Hi!

I have a similar problem. I just installed Ubuntu Feisty, and I can not make my microphone working.
The previous distrib was a Gentoo, and the microphone worked fine.

Any idea?

---

