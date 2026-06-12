---
title: "Recent updates break headphone output on Samsung laptop"
date: 2010-10-03
forum: Multimedia Software
---

### Post by cdyson37 on 2010-10-03
I thought I'd post the solution here to save anyone else in the same situation having to google as much as me!

I have a Samsung R510. Plugging in headphones does not mute the sound from the internal speakers, and no sound emits from the headphones. Some details:
```
 $ cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC262
Codec: Intel G45 DEVCTG
```

Anyway it seems to be fixed by loading the module thus
```

modprobe snd_hda_intel model=ultra

```

Adding the following line to /etc/modprobe.d/alsa-base.conf should solve the problem for good:
```

options snd-hda-intel model=ultra

```

---

