---
title: "ALSA and timidity"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by coral on 2007-02-18
Hello, i am trying to activate Timidity Trough ALSA to run rosegarden properly
**I do this: **timidity -iAD -Os
**And i get this:** Requested buffer size 32768, fragment size 8192
ALSA pcm 'default' set buffer size 33868, period size 3760 bytes
TiMidity starting in ALSA server mode
ALSA lib seq_hw.c:472:(snd_seq_hw_open) SNDRV_SEQ_IOCTL_PVERSION failed: Inappropriate ioctl for device
error in snd_seq_open

What is wrong, and what can i do to correct it?

/Many thanks from coral

---

### Post by lhtown on 2007-02-19
I am not at all sure, but it looks like maybe either your sound card doesn't do MIDI (a lot of cheap ones don't) or else timidity can't figure out how to make it work.

You may have to upgrade your sound card.

---

