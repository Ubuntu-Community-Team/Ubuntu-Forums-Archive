---
title: "ffmpeg - remove an audio stream from mpg"
date: 2009-05-04
forum: Multimedia Software
---

### Post by rick71 on 2009-05-04
I would like to remove an audio stream from some mpgs my camera generates.
ffmpg -1 shows the following:

Input #0, mpeg, from 'hpim0212.mpg':
  Duration: 00:00:04.08, start: 0.122878, bitrate: 1916 kb/s
    Stream #0.0[0x87]: Audio: liba52, s16
    Stream #0.1[0x1e0]: Video: mpeg1video, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 104857 kb/s, 24.00 tb(r)
    Stream #0.2[0x1c0]: Audio: mp2, 44100 Hz, mono, s16, 96 kb/s

Can anyone tell me how to remove that first audio stream using ffmpeg or something else?

Thanks.

---

### Post by FakeOutdoorsman on 2009-05-04
Try this:
```
ffmpeg -i hpim0212.mpg -map 0:1 -map 0:2 -acodec copy -vcodec copy hpim0212b.mpg
```
The *-map* option corresponds with each stream.  The *-acodec copy* and *-vcodec copy* options tell FFmpeg to just copy the streams.  No re-encoding necessary.

---

### Post by rick71 on 2009-05-04
Thanks.

---

