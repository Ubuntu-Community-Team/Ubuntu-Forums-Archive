---
title: "Botched OSS4 installation -&gt; ALSA broken"
date: 2010-08-16
forum: Multimedia Software
---

### Post by ljp37 on 2010-08-16
Hi all,

After trying to unsuccessfully install OSS4, it seems I've broken ALSA and have no sound.  I've uninstalled the oss4 packages and rebooted, and now alsamixer reports "cannot open mixer: no such file or directory".  Here's the output of aplay -l:

```

**** List of PLAYBACK Hardware Devices ****
aplay: device_list:244: snd_ctl_pcm_next_device

```

PulseAudio also doesn't find any hardware devices, though it is able to play to the Apple Airport Express down the hall.

I'm running 10.04 64-bit on a Thinkpad X61.

Any help very much appreciated.

---

### Post by ljp37 on 2010-08-16
Huh. It fixed itself after I put the computer to sleep and woke it up. Yay.

---

