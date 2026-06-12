---
title: "Problem with PulseAudio and 2 Sound Cards"
date: 2009-04-25
forum: Multimedia Software
---

### Post by xpan on 2009-04-25
Hi,

I have two sound cards. One is internal and on Board (standard RealTek) and one is an external USB Edirol UA-20. Both of them have been successfully identified by Ubuntu 9.04

My problem is that I want to use my External USB as my default card. This is happening only if I select System->Prefs->Sounds and choose "Edirol UA-20 (OSS)". Any other selection leads to no sound.

I Have installed PulseAudio Device Chooser and selected as my default Sink the Edirol card. But still, if I choose PulseAudio in Sound settings I still get no sound. Only Edirol(OSS) seems to be the right choice. Strangely enough if I choose just "OSS" I get sound from my internal Realtek card. To make matters worse, when I select Edirol (OSS) from the sound settings I get no sound when playing flash videos (e.g. Youtube). Even more strangely although Alsaservice is up, when I choose (Alsa) in the sound settings the windows stops responding and I have to "kill -9".

I did what it says here: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

but still I get no sound when I choose PulseAudio from the sound settings. 

Any ideas?

---

