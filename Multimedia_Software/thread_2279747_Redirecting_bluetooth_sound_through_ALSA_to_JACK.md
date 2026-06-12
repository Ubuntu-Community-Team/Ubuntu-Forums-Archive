---
title: "Redirecting bluetooth sound through ALSA to JACK"
date: 2015-05-25
forum: Multimedia Software
---

### Post by jbb3 on 2015-05-25
Hi, I'm trying to stream from my phone to the computer and then to go through JACK and going out again to the speakers.
I've removed completely PulseAudio and I lost the streaming (phone-computer-PA-ALSA-speakers), which was perfectly working with A2DP after generating a loop inside the PA.

The idea is to connect again everything with JACK (I really need this server) as an audio server (phone-computer-JACK-ALSA-speakers).
Tried:
- .asoundrc generate a bluetooth device, not success as the only device generated was an output bluetooth device
- .asoundrc redirect all the ALSA as default to JACK, not working, seems like the bluetooth streaming is not directly connected to ALSA.

Any idea?

Thank you

---

