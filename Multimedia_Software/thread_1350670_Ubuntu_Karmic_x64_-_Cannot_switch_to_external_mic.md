---
title: "Ubuntu Karmic x64 - Cannot switch to external mic"
date: 2009-12-09
forum: Multimedia Software
---

### Post by f1ckratte on 2009-12-09
Hi guys.

I have an HP dv5 1040eg and a sound chip with the codec IDT 92HD71B7.
I have three jacks in front of my Laptop, two jacks for headphones and one for the mic. Normally theres a jack-sense which reacts to the plugging of a connector to the jacks and then turns of the internal Hardware.
The two headphone connectors work perfectly but the mic jack-sense doesn't work. When i plug it in i still have the internal mic as input source, its sound quallity really is terrible.

I have Alsa 1.0.21 and the latest Pulse audio

I allready tried adding ```
options snd-hda-intel model=hp-dv5 enable_msi=1
options snd-hda-intel model=hp-dv5
options snd-hda-intel model=3stack
```
to Alsa-base.conf

Hope you guys can help me.

---

