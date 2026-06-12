---
title: "Sound - Dynamics processor for line input?"
date: 2012-07-14
forum: Multimedia Software
---

### Post by tubezninja on 2012-07-14
I'm wondering if someone here has experience with this problem and can help me out with a software solution.

I have an audio stream that is being sent out from an Ubuntu 12.04 desktop, from a line-in source.  It's not a high-fidelity affair at all, just some amateur radio-type VHF stuff being fed from a receiving radio to a 16 kbps mono audio internet stream using IceCast.

The problem is, signals are being received from multiple sources, from varying distances and setups, and so the audio is coming in all over the volume spectrum... some inputs are really loud, others very soft.  The dynamic range, as a result, is pretty high and can be uncomfortable to listen to at times.

What I'd like to do is process this audio before it gets fed to icecast, gating the dynamic range so that the higher-volume sources are potted down somewhat, and maybe even amplify the softer sources.  Ideally, it would be nice to have each source be sent over the stream at a uniform volume.

An added bonus would be: there's a small amount of 60Hz hum leaking into the audio despite my group loop filtering attempts, that I'd like to gate out out as well.

There's plenty of hardware gates and audio processors that do this, but they can be pricey.  If there's way to do this with the desktop receiving the audio and some software, that would be great. Does anyone know if this can be done?

Thanks!

---

