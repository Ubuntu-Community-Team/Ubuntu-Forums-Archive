---
title: "Hardy INTEL-HDA Mic SOLVED"
date: 2009-03-07
forum: Multimedia Software
---

### Post by mastermindg on 2009-03-07
I recently solved an issue related to Skype on Hardy. My sound card is an Intel HDA 3Stack. My sound worked perfectly except for the MIC input. I could hear my voice on a recording, but it was VERY low. So, I followed every step imaginable to setup my default-card and added the 3stack model line on the alsa-base config, etc. None of this helped AT ALL.

In the end, all I had to do was turn the MUX input on. Once I did this my MIC came to life and it records fine now. I just wanted to share this with anyone who may have a similar incident in the future.

**Try turning on MUX (or all inputs under Recording) first before you go any further with troubleshooting.**

By the way, I've removed Pulseaudio from boot and I feel like a HUGE weight has been removed from my shoulders. I know that Pulseaudio has been included with the best intentions, but it has been a bane of Ubuntu's existence ever since.

---

