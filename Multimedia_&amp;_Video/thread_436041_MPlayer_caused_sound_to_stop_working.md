---
title: "MPlayer caused sound to stop working"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Count on 2007-05-07
I'm on a kubuntu 64 bit edgy box.  Anyway, I installed mplayer to try and play some .wmv files, and I was getting a video out error, so I went into the mplayer preferences, and changed the video and audio drivers a few times, trying to get mplayer to work. After that, BMP and all other audio, except for the system beep at startup, has no sound. 

```
aplay -l

 **** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I also tried to fix the problem by purging mplayer and reinstalling it, but no go.

Edit: I forgot to mention that I also reinstalled the alsa drivers with apt-get.

---

