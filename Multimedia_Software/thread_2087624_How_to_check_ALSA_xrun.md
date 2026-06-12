---
title: "How to check ALSA xrun ?"
date: 2012-11-24
forum: Multimedia Software
---

### Post by gdmn1973 on 2012-11-24
Hello,

i am using Ubuntu studio to record analog audio with Audacity and an external DAC which is connected via USB. I prefer to avoid jackd and i setup Audacity to record directly from the DAC as an ALSA device.

I would like to check if XRUNs occur, but there are no xrun_debug entities under /proc/asound/cardxx. Is there any alternative way check for XRUNs in ALSA or i have to rebuild the kernel with options like CONFIG_SND_PCM_XRUN_DEBUG ?

---

