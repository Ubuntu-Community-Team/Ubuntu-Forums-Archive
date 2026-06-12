---
title: "Stream-based output autoswitching in Pulseaudio?"
date: 2011-07-12
forum: Multimedia Software
---

### Post by alexander750 on 2011-07-12
A few days ago I had posted a question about getting PCM and AC3 audio out of the same S/PDIF output on my sound card (along with analog, out of another output). The post was [here]("http://ubuntuforums.org/showthread.php?t=205449&page=193") (look for #1925).

To answer my own questions: (1) yes, it is possible to use analog and S/PDIF simultaneously; in my .asoundrc file, I'd need to define one output as the default, and the other as a slave. As for (2), it might be possible, if there were some way for Pulseaudio to know where to direct different kinds of streams.

For example, suppose I've defined two different digital outputs in .asoundrc. One is a stereo LPCM mixdown, which I'll call "digital_mixed", to be used most of the time (e.g., in Banshee, Audacity, desktop sound effects, etc.) The other is a raw dump directly to S/PDIF, which I'll call "digital_raw", and which will be used only with AC3 streams (typically Dolby Digital or DTS from a DVD player, but could also be from a DTV tuner in MythTV).

The reason for wanting these particular outputs is my HT amp only recognizes two kinds of digital input: (1) uncompressed LPCM stereo at 32, 44.1 or 48 kHz, 16 or 24 bit, and (2) AC3, at the bandwidths typically used for Dolby Digital or DTS. That's it.

Currently, I have PCM--and *only* PCM--output from that S/PDIF port. The reason is simple: I don't know how I might switch between "digital_mixed" and "digital_raw", other than constantly editing .asoundrc depending on whether or not I wanted to watch a DVD!

Is there a way to get Pulseaudio to do this automatically, i.e., to specify AC3 be sent to "digital_raw" and all other streams be sent to "digital_mixed"?

---

