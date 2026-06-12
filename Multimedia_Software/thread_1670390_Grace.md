---
title: "Grace?"
date: 2011-01-18
forum: Multimedia Software
---

### Post by chaco479 on 2011-01-18
has anyone used Grace, the "algorithmic music composer" before? I am trying to learn it, and cannot seem to get it to connect properly to Jack.  My sound card uses alsa, and no matter what settings I use I cannot figure out how to hook up midi to get sound to play from Grace.  I looked through the documentation on the website but it is entirely focused on writing code, not on getting it set up.  I'm a bit of a n00b when it comes to music and midi in linux, so any help would be greatly appreciated

---

### Post by BicyclerBoy on 2011-01-18
Have not used Grace but..
To play midi from RoseGarden you need fluidsynth & the soundfonts packages.
(all in synaptic)

You also need to understand how to wire up jack.
AFAIK Jack connects directly to alsa kernel modules for audio device.
It does not share the audio device.

---

