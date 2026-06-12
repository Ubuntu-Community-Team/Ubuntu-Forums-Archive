---
title: "Realplayer 10 and default soundcard"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by chriswyatt on 2007-02-27
Basically, the problem is, I have two soundcards, one is internal (HDA Intel), the other is external (USB Audigy 2 NX).  The USB Audigy 2 NX is set as default but Realplayer insists on using the on-board Intel soundcard, also the sound is choppy and I think the USB soundcard is better supported, so I'd prefer to use this.  Also, I can't connect my internal soundcard up to my speakers due to driver limitations (headphone port not working), thanks for your time.

By the way, I tried the method recommended in the Readme file that came with Realplayer: export AUDIO=/dev/dsp1 , but this did not work and Realplayer carried on using my internal soundcard.

---

### Post by chriswyatt on 2007-02-28
Bump:  I reckon Realplayer could be using OSS instead of ALSA, when I test OSS I also get sound from my on-board soundcard. Could I get my Audigy 2 NX as default through OSS as well?

---

