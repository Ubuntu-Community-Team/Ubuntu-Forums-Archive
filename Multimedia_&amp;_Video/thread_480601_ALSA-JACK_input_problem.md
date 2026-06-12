---
title: "ALSA-JACK input problem"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by darsu on 2007-06-21
I have an SB Live card on a Kubuntu 6.10 system. On my previous installation (Kubuntu 5.10) JACK worked fine.

On this new OS installation,  sound entering the soundcard Line In does not reach the JACK layer. The sound does get through to ALSA, because I can use eg. alsamixer to adjust levels, and sound is heard at the soundcard output. If I use QJackCtl to patch the "alsa_pcm capture" input (which is the only external input available to JACK) through a JACK-aware mixer/EQ, I can see there indeed is no signal from that input at all; if I replace the input with that from a software synth, everything works.

What could be the reason for the JACK network not receiving anything from the ALSA PCM input?

---

