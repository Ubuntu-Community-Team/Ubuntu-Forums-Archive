---
title: "Jack Problem - Sounds like Robotic Chipmunk"
date: 2011-02-12
forum: Multimedia Software
---

### Post by alchemist23 on 2011-02-12
I am experimenting with a system using 3 5.1 channel sound cards (2 SB Lives and an Audigy 2 ZS).  My goal is to be able to plug a mic into one port on one card and route it out any number of other ports via Jack Mixer.  I currently have the output sort of working.

I'm using alsa_in and alsa_out to bring the extra cards on-line then adding a mic channel and the appropriate output channels to Jack Mixer.  Once the cards are online and the mixer channels are active, I set up the connections in the QJackCTL Connections panel.  When I un-mute the Mic and talk, I hear my voice on all the output channels, but it sounds like a robotic chipmunk.  I.e. the pitch is way to high, like it's been speed up, and there is a "vibration" to the sound almost like it's going through a ring modulator.  This would all be well and good if the intent was to sound like a Dalek on crack, but that is not the case.

I thought that possibly the clocking between the other cards might be an issue, so I tried removing all but the Audigy 2 ZS and just using it's mic and front channel outputs.  Unfortunately the result is exactly the same.

Turning realtime off or on makes no difference either, nor does adjusting the sample rate or buffer.

Any ideas what my problem could be?  (I am using Jack1 not Jack2)

---

