---
title: "Audio died after last update"
date: 2009-04-08
forum: Multimedia Software
---

### Post by pooppoop on 2009-04-08
I updated using the update manager and rebooted as requested.
When i booted up i had no sound.
When i try to start alsa:
```

**sudo alsa reload**
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/pooppoop/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-pcm-oss snd-pcm snd-page-alloc snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-pcm-oss snd-pcm snd-page-alloc snd-mixer-oss snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.

```

and trying to run alsamixer give me:
```

**alsamixer**

alsamixer: function snd_ctl_open failed for default: No such file or directory


```

---

### Post by ekidd91 on 2009-04-08
I'm having a similar problem, are you getting any of the volume control error messages I'm getting?

[http://ubuntuforums.org/showthread.php?t=1119588](http://ubuntuforums.org/showthread.php?t=1119588)

---

### Post by Zeedok on 2009-04-08
Me too.  I just posted this problem in the [general forum]("http://ubuntuforums.org/showthread.php?t=1119573").

I tried:

```
sudo reload alsa
```

and it appeared to unload and reload everything fine.

What else can we try??

---

### Post by pooppoop on 2009-04-08
> **ekidd91 said:**
> I'm having a similar problem, are you getting any of the volume control error messages I'm getting?

[http://ubuntuforums.org/showthread.php?t=1119588](http://ubuntuforums.org/showthread.php?t=1119588)

yes it does.

---

### Post by pooppoop on 2009-04-08
i found a temporary solution.
I reverted to the older kernel(before the update)
from 2.6.27.11
to 2.6.27.9

but that isn't a good solution, hopefully it will be fixed soon

i guess the driver for sis audio isn't compatible with the newer kernel

---

