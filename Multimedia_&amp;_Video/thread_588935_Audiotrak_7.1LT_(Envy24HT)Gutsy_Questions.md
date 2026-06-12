---
title: "Audiotrak 7.1LT (Envy24HT)/Gutsy Questions"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by shrubman on 2007-10-23
Hi folks,

I'm new to Linux but have reviewed numerous sources of information regarding sound issues and how to solve them. Even so, I have not found any answers to my questions (note: I have just reinstalled Ubuntu from the Gutsy live disk and have not changed any settings):

1) aplay -l gives me:

 List of PLAYBACK Hardware Devices ****
card 0: LT [Audiotrak Prodigy 7.1 LT], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: LT [Audiotrak Prodigy 7.1 LT], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: LT [Audiotrak Prodigy 7.1 LT], device 2: ICE1724 Surrounds [ICE1724 Surround PCM]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2

That is the correct card. IEC958 is s/pdif, right? What's up with the ICE vs. IEC entries? Is that a spelling error and could it cause problems?

2) In menu System>Preferences>Sound, I am offered the following options for each item:

Autodetect
ICE1724 Surround PCM
IEC1724 IEC958
ICE1724
ALSA
ESD
OSS

The only one that makes a sound when I hit the test button is IEC1724 IEC958. Given that I am connected to my receiver only through the coax digital out from my card, is that what I should expect?

My music plays through my receiver, seemingly fine, but the volume control and alsa mixer have me confused. The alsamixer says it is controlling the chip ICE1724 multi-track. Is that what I want? How can I change that? In my volume control applet , whether I set it to control "Audiotrak Prodigy 7.1LT (Alsa Mixer)" or "ICE 1724 Multitrack (OSS Mixer)" the volume slider produces no effect.

3) Why can I not get any of the system sounds to play on the Sound tab of System>Preferences>Sound?

4) I do not get any sound from Firefox plugins. Is that a related problem or a separate issue?

Thanks all!

---

### Post by shrubman on 2007-10-24
If no one can answer my questions specifically, can you tell me if the actions suggested in the "Comprehensive Sound Problems Solutions Guide" are still accurate?

---

