---
title: "Digital Sound Issues"
date: 2009-09-21
forum: Multimedia Software
---

### Post by doesntcount on 2009-09-21
I'm hoping I can get some advice on solving, what I am finding is a very complicated problem to solve, despite my very simple requirements. All I want is to be able to play digital sound out my sound card's S/PDIF interface from various software running in ubuntu. This software includes, but is not limited to: firefox (flash), audacious, and mplayer.

These requirement are not satisfied out of the box. Currently, I can get gnome's sound settings to play to the alsa plugin, which plays digital out my s/pdif interface. Firefox plays no sound at all. And audacious will only play analog out the s/pdif interface.

I've recently learned about Pulse Audio Sound Server, which manages sound between different applications. Is this necessary to satisfy my requirements? Or should I be able to get this to work without setting up Pulse Audio?

Any help out would be greatly appreciated. Thanks in advance to anybody that's able to help.

---

### Post by doesntcount on 2009-09-23
No pointers at all?

---

### Post by doesntcount on 2009-09-24
Can someone at least tell me if they think it's worth going down the path of setting up Pulse Audio to solve this issue? Or is that not likely to help?

---

### Post by doesntcount on 2009-09-26
Alright, for anyone else that's having issues similar to mine, pulse audio is totally the way to go. Firefox and audacious are both playing out my spdif interface. Things are looking much better.

This howto proved very helpful:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

I have one outstanding issue, however. On my old motherboard (that I had to replace because some capacitors exploded) I could play out the spdif interface and use a Y-splitter to send the digital signal to two different dts decoders. It was great because i had sound playing on two different floors of my house. However, I can't do that currently. It plays out only one of the splits.

Anybody have ideas on how to get this working again? I'm afraid i'm totally out of my league regarding expertise in this area.

Thanks to anybody that can provide some advice.

---

