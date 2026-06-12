---
title: "[SOLVED] Slow opening audio and video file"
date: 2008-10-12
forum: Multimedia Software
---

### Post by zelan on 2008-10-12
Hi,

I've searched all over and couldn't find a solution to my problem.

For whatever reason, whenever I open an audio or video file, the program (using either Totem or Exaile) takes a long time to load the file.  The delay is around 20 seconds.  This delay also occurs when switching to another song in a playlist.  After the audio/video actually starts playing, there is no studdering or other problems for the rest of the file.

Oh, and this hasn't happened before and I've been running Ubuntu for months now.

---

### Post by zelan on 2008-10-13
Fixed!

Just restore the alsa configurations to their original settings as per the instructions at [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

```
sudo apt-get --purge remove alsa-base alsa-utils
sudo apt-get install alsa-base alsa-utils
```

---

