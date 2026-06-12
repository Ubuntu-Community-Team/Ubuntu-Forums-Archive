---
title: "bluetooth audio"
date: 2022-04-19
forum: Multimedia Software
---

### Post by bjlockie on 2022-04-19
If I add a bluetooth USB dongle to my desktop will I be able to pair with a bluetooth speaker and get audio?

If bluetooth audio better than aux?

---

### Post by Holger_Gehrke on 2022-04-21
Short answer: Yes and No.

Yes, Bluetooth audio does work (I often use Bluetooth headphones to listen to music while doing other stuff around my flat). Might take a bit of configuration, I remember having to change the Pulse Audio configuration to load a module for Bluetooth. How difficult this will be in your case largely depends on the dongle you buy. Most work out of the box.

No, the quality of Bluetooth audio is very slightly worse. Depending on the transfer profile used it can range from horrifying (HSP - Head Set Profile; that's really only meant for voice transmission from a phone to a head set) through good enough (A2DP - Advanced Audio Distribution Profile; uses a lossy compression called SBC so you have a decompression from whatever format your audio starts out in followed by a compression using SBC , which means there's a bit of additional loss compared to listening through a direct wired connection) to the various proprietary high-quality Bluetooth audio profiles (aptx etc) which are AFAIK not supported on Linux. A good set of wired active speakers (basically loudspeakers with a built-in amplifier) will sound better (and there's also the question of stereo - you can't get stereo with only one speaker ....) and have far less lag (all the decompressing, recompressing, transmitting and decompressing takes some time, so forget about gaming using Bluetooth audio).

Holger

---

