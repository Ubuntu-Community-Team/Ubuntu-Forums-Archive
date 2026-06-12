---
title: "Low mic volume on Dell XPS M1330 10.10"
date: 2011-01-07
forum: Multimedia Software
---

### Post by thetechnaddict on 2011-01-07
Horrible time looking for solutions - turned out to be easy and nothing like the various other posts I found that involved tweaks to alsamixer or installing kMix (don't go there!) or rubbing garlic on the sound card. 

There's a post all about it here:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

It it it tells you how to identify your sound card, and find the right options to put into the end of

/etc/modprobe.d/alsa-base.conf

for me it was:

options snd-hda-intel model=dell-bios

Works a treat without getting installing loads of stuff you will never need.

---

