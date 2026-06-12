---
title: "audio recording clicks"
date: 2014-07-27
forum: Multimedia Software
---

### Post by lowdx1 on 2014-07-27
i installed 14.04 which is great but i have one little problem.

when using Audacity (or arecord) to record sound with my microphone i can hear clicks. it's not due to clipping the preamp but plain annoying clicks.

i'm using ASRock's 960GM/U3S3 FX internal sound card (Realtek ALC662).

---

### Post by tgalati4 on 2014-07-28
Because the sound chip is on the motherboard, it is likely to pick up noise--there is no way to shield it.  Try using a USB-preamp.  You will be sending a line-level signal into your sound card and that can push the noise level to near-inaudible levels.

Is this machine dual-boot?  Do you get noise in Windows?

---

### Post by lowdx1 on 2014-07-28
it is no noise but clicking. i'm not getting it on windows. clicking such as this occurs due to low buffer-size usually but i can't find a way to configure it in alsa.

---

