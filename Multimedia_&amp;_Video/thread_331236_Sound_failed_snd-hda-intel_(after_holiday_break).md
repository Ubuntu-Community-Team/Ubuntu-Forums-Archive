---
title: "Sound failed: snd-hda-intel (after holiday break)"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by OsireS on 2007-01-04
Hi everybody

I was away from my university PC over the holidays (from about the 20th of December) and came back today and ran the update manager (it specified a whole lot of upgrades). After this occurred I lost my sound :( and when I run modprobe for snd-hda-intel I get the following errors:

```
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-10-generic/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.17-10-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Anybody have any ideas whats going on and how I can fix this? Running standard versions of ALSA and the kernel as well as the Nvidia driver (thought it might be my BETA Nvidia driver causing issues with a kernel update so I've now downgraded to the standard Nvidia driver that comes with edgy).

Any help would be appreciated :)

---

