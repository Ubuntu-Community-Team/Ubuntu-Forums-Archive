---
title: "audio device in ubuntu 10.10"
date: 2010-12-01
forum: Multimedia Software
---

### Post by me.translucent on 2010-12-01
i am trying to use lingot application for tuning my guitar , but turns out it has some bug and won't detect my audio,i have a faint recollection of getting it to work by some tinkering . i tried fiddeling with the setting and i saw that device file that it is using under the tab OSS is /dev/dsp which is non existant , is there a new device file for that in ubuntu 10.10

---

### Post by cbrey54 on 2012-01-14
Set edit  -> Preferences -> Audio dev to "default"
Edit ~/.lingot/lingot.conf so that
AUDIO_DEV = /dev/audio1

Save, close, restart Lingot.

Cheers

---

