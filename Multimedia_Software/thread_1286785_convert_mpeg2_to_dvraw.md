---
title: "convert mpeg2 to dvraw"
date: 2009-10-09
forum: Multimedia Software
---

### Post by zelenka on 2009-10-09
I would like to convert a mpeg2 video to a dvraw video, i tryed with ffmpeg but the output video is distorted.

here, the command i tryed
```

djo@ctdjo:~$ ffmpeg -i ./Bureau/Mov.MOD -target pal-dv ./Bureau/Mov.dv
...
Input #0, mpeg, from './Bureau/MOV01B.MOD':
  Duration: 00:00:21.12, start: 0.227389, bitrate: 10059 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 16:15 DAR 4:3], 9600 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 256 kb/s

Output #0, dv, to './Bureau/Mov.dv':
    Stream #0.0: Video: dvvideo, yuv420p, 720x576 [PAR 16:15 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
...

```anybody can help me? 
thks

---

