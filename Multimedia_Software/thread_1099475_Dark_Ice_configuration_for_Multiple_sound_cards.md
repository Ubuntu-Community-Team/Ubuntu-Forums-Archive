---
title: "Dark Ice configuration for Multiple sound cards"
date: 2009-03-18
forum: Multimedia Software
---

### Post by higorav on 2009-03-18
Hi,
I am using DarkIce to fetch the audio stream from the sound card. The configuration for the single sound card looks like this:

[general]
duration        = 60
bufferSecs      = 5

[input]
device          = /dev/dsp
sampleRate      = 22050
bitsPerSample   = 16
channel         = 2

I was wondering if we've got multiple sound cards, what would be the device name used here for the second icecast instance running for the second sound card. Any help would be highly appreciated.

Thanks!!!

---

### Post by q.dinar on 2011-12-05
i want also to know this, now i use it with device=default and i can select soundcard which i want with pulseaudio volume control. but i would use alsa instead of pulseaudio because if i am not mistaken, it uses less cpu and maybe would work without desktop.

---

