---
title: "why the sound from CD-input is mono?"
date: 2009-09-26
forum: Multimedia Software
---

### Post by ooli on 2009-09-26
Dear forum members,

Today I (clean) installed Jaunty in the hopes of sorting out the mess I made while trying to get sound from my tv tuner. 

This time, the instructions [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) helped me get sound from my saa713* tv tuner, which is connected to the soundcard's CD plug using an internal audio cable (the tuner doesn't have line-out).  However, the sound is mono, but it should be stereo. 

Any idea what could be causing this and what could be done to get stereo sound from the CD?  It's the only sound that plays in mono.  Please let me know if you need any output from Terminal or any other information that could be useful.

Could I be using the wrong model option for my soundcard in alsa-base.conf? (I'm currently using "6stack-dig, which I think is the right one)

Thanks!

---

### Post by ooli on 2009-10-17
Still unable to get stereo audio from CD. :(  If it makes any difference, I'm only getting sound from the right channel.

I tried several model options in alsa-base.conf, tried another internal audio cable, upgraded to the newest alsa driver - no improvement. 

I noticed other people are also having problems with mono audio and it appears they haven't been able to sort them out either...

Any suggestions?

---

