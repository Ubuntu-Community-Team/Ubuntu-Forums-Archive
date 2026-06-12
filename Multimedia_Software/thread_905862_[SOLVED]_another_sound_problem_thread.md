---
title: "[SOLVED] another sound problem thread"
date: 2008-08-30
forum: Multimedia Software
---

### Post by gummygod on 2008-08-30
I have an creative audigy sound blaster sound card (ca0106), yes I know it has issues. I have had surround sound working on it a while ago, but i decided to mess around trying to get multiple sources to play simultaneously.  I messed around with pulse audio and I got 2.1 sound and multiple sources. I have a 5.1 set up and would rather have surround sound than multiple sounds so I dont care if its just back how it was. I messed around with pulse audio settings changing the default channels to 6.  I tried uninstalling everything pulse audio related and also switching between alsa and pulse audio in programs and defaults. Nothing will give me more than 2.1 sound. 
Anyone have ideas? and what more info do you guys need?

Thanks a ton

---

### Post by gummygod on 2008-09-01
hrmmm running pulse audio displays this:

```
W: alsa-util.c: Device hw:0 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
W: alsa-util.c: Cannot find fallback mixer control "PCM".
W: alsa-util.c: Device hw:0 doesn't support 6 channels, changed to 2.
W: alsa-util.c: Device hw:1 doesn't support 6 channels, changed to 2.

```

so must be something wrong with pulseaudio cause both chips should do 7.1. Is there a way to start from scratch on sound? cause alsa worked fine for one channel at a time, then when i messed with pulseaudio it broke surround.  id appreciate any help.

---

