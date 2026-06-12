---
title: "VIA VT1708B (Intel HDA): changing volume just changes equalization"
date: 2011-05-08
forum: Multimedia Software
---

### Post by aldimond on 2011-05-08
What I'm running: 64-bit Kubuntu 11.04.

What I have: I have some fancy-pants onboard sound card with too many outputs (7.1), as does pretty much everyone these days. Specifically mine is a VIA VT1708B. I have a good old stereo receiver plugged into it. There are headphone/microphone jacks on the front panel of my computer but they're affected by electrical interference and thus subject to annoying chirps based on I/O, hard drive activity, etc... so they're dead to me.

What I want: I want stereo audio at line level coming out any one of the cryptically-labeled jacks on the back of my computer. It would be nice if I could scale that audio signal down using the system volume slider.

What I'm getting now: I can hear output. When I change the system volume the equalization changes but not the actual loudness. If I turn the system volume all the way up or most of the way down equalization sounds OK, in between it mostly cuts the low frequencies out.

My current config and other stuff: I have an "Analog Stereo Duplex" profile selected. My "Backend" is the "Phonon GStreamer backend".

Interesting stuff: If I open a terminal and run alsamixer (now I'm in my comfort zone!) I can make things work exactly like I want by setting "Surround" to 0. If I then adjust "Master Front" it makes things louder and quieter. BUT. It I touch any of the KDE controls it sets "Surround" back to full, and everything is bad again. Also if I reboot my computer the "Surround" slider is back up and the volume does equalization again.

ZOMG HALP! I guess what I mean is, how can I make my ALSA mixer settings persist, and make KDE/GStreamer/whatever stop screwing with things (except for the "Master Front" slider)? Or, alternately, any other way of making the system volume control work like a volume control...

(As a ranty aside, I once tried to implement a really simple Intel HDA simulator for QEMU, and found that Intel HDA is just stupidly complicated and packed with metafeatures, even compared to something like AC97, which is pretty flexible... if there's a driver bug affecting certain random HDA boards that wouldn't surprise me....)

---

