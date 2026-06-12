---
title: "VLC: no sound from capture device"
date: 2009-11-07
forum: Multimedia Software
---

### Post by King_Critter on 2009-11-07
I have a Hauppauge PVR-150 capture card. When I try to use VLC to play watch something through it, the video comes through fine, but the audio fails.

```
VLC is unable to open the MRL 'alsa:///dev/video0'. Check the log for details.
```

However "cat /dev/video0 > movie.mpg" *does* give me the audio, so I know it's not a hardware problem.

Any ideas?

---

