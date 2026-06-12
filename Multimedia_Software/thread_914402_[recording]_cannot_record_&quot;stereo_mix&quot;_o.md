---
title: "[recording] cannot record &quot;stereo mix&quot; of soundcard"
date: 2008-09-08
forum: Multimedia Software
---

### Post by kakyoism on 2008-09-08
I used to record "stereo mix" of soundcard output on Windows.
Read a few tutorials about using the "arecord" command to do the same thing on Linux,

However, using the following command only gives me the microphone input:
```
arecord -d 10 -f cd -t wav -D hw out.wav
```

which means, if I unplug the mic, I will hear nothing.

Is there a way to record the digital output or even back-end audio samples of the "stereo mix"?

Thanks!

---

