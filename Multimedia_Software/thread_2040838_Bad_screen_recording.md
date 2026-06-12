---
title: "Bad screen recording"
date: 2012-08-11
forum: Multimedia Software
---

### Post by Halbblutplins on 2012-08-11
I tried to record my desktop ffmpeg but i  get so bad results, it seems i recorded with only 5fps but i recorded  with 30fps. I also get with kazam, eidete, recordmydesktop and xvidcap  so bad results. :sad: With ffmpeg I also tried many codecs but nothing helped.

ffmpeg code:

```
ffmpeg -f x11grab -s hd1080 -i :0.0 -r 30 -qscale 1 -vcodec mpeg4 /home/*****/testvid.mp4
```

My system specs:
- AMD Phenom(tm) II X4 3Ghz
- Geforce GTX 550ti by Club3D
- 8GB DDR3
- Ubuntu 12.04
- video driver 295.71
[B]
*Update: I tried to record only a little part of my desktop and voila, the recording was smooth. Is it possible that the problem my PCIE is because I have PCIE 1.0 ???[/B]

---

