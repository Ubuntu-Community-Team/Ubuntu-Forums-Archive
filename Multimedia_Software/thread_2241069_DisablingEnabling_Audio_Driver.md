---
title: "Disabling/Enabling Audio Driver"
date: 2014-08-24
forum: Multimedia Software
---

### Post by chenfeif on 2014-08-24
I have an issue where if I plug in my speaker, my audio driver instantly mutes itself and then cannot be unmuted. This happens 50/50 and the solution I found when I was using windows was to go into devices and disable/re-enable the audio driver. I was wondering if there is a way to do the same in Ubuntu?

I tried lsmod/rmmod on the snd_hda_intel.ko and soundcore.ko but there were too many dependencies.
I tried to go into the pci and make it unbind (the audio driver is connected via pci) from sys/bus/pci/drivers/snd_hda_intel, but it said permission denied even when I did "sudo echo "0000:00:1b.0" > unbind

Is there some easy way to load/unload the sound driver in linux? Thanks.

---

### Post by Yellow Pasque on 2014-08-24
Try:
```
sudo alsa force-reload
```

---

