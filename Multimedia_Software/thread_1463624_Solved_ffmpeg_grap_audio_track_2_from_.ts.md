---
title: "Solved: ffmpeg: grap audio track 2 from .ts"
date: 2010-04-27
forum: Multimedia Software
---

### Post by Lampi on 2010-04-27
Hello

Here's what I have from a tv recording:

```
Stream #0.0[0xa4]: Video: mpeg2video, yuv420p, 720x576 [PAR 64:45 DAR 16:9], 15000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x60](fra): Audio: mp2, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.2[0x61](eng): Audio: mp2, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.3[0x62](dua): Audio: mp2, 48000 Hz, stereo, s16, 192 kb/s
```
How do I extract the English audio track without demuxing the stream?

this selects the French stream only:
```
ffmpeg -i <inputfile>.ts -acodec copy -vn <outputfile>.mp2
```
How do I select stream #2?

---

