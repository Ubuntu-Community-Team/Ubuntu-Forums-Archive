---
title: "audio sounds watery"
date: 2010-01-26
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-26
In mythbuntu 9.10 my audio sounds watery and digital when it gets too loud.  I have the sound set to use /dev/dsp1 which is my tuner card.  My sound card (SB Audigy) is at /dev/dsp.  I have an 1/8" plug in my sound card and the other end of the 1/8" cable goes into an aux input on an HD radio.

What am I doing wrong here?  I don't get any sound if the backend sets the audio to use /dev/dsp (my sound card).

---

### Post by linuxhippy on 2010-01-26
Got it to sound perfect.  My capture card is a Pinnacle 800i.  On the backend I had to change the sample rate to 4800.

---

