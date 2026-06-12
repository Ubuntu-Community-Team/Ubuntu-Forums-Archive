---
title: "Dell Inspiron One no sound"
date: 2013-11-07
forum: Multimedia Software
---

### Post by ryan-hoboabode on 2013-11-07
I cannot seem to get sound working on my Dell Inspiron One 2305 running 13.10 (or on 13.04).  I've tried every combination I have found for alsa-base.conf but no dice.  Anyone here have any ideas?

[http://www.alsa-project.org/db/?f=6d7eb08334e19274e9de7a5c5605df72889a1873](http://www.alsa-project.org/db/?f=6d7eb08334e19274e9de7a5c5605df72889a1873)

---

### Post by Yellow Pasque on 2013-11-09
I'd file a bug on this one (and post the link to it):
```
[  964.967893] hda_codec: ALC272: SKU not ready 0x598301f0
```

Your model may need a line similar to: [https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c#L4618](https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c#L4618)

---

