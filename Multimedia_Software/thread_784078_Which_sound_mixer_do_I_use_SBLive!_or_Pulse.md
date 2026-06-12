---
title: "Which sound mixer do I use? SBLive! or Pulse?"
date: 2008-05-06
forum: Multimedia Software
---

### Post by timzak on 2008-05-06
I'm not quite sure I understand everything about this new PulseAudio in Hardy, but I noticed in my Volume Control Preferences that it is set to SBLive! [CT4620] (Alsa mixer).  There is also an option for:
Playback: ALSA PCM on front:0 (ADC Capture/Standard PCM Playback) via DMA (PulseAudio Mixer)

Do I need to set it for the 2nd option in order to be using PulseAudio?  Not sure here what this should be set to.

Any help greatly appreciated.

Thx.

---

### Post by kostkon on 2008-05-06
You can select your mixer in *System -> Preferences -> Sound*. Currently , it should be set to *auto*, and that means that you are using *PulseAudio* for your mixing, which is a software mixer.

If you want to use the hardware mixer then set your playback to *Alsa*. The *Alsa* driver has very support for the hardware mixer of *Creative Live!* with the ability for simultaneous 100+ channels without any CPU usage.

*PulseAudio* offers good things like volume levels for every app and many other cool stuff.

The *Alsa* driver for *Live!* offers good hardware mixing.

You decide!!

---

