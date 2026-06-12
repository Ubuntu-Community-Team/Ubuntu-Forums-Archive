---
title: "render time cut in half"
date: 2013-01-14
forum: Multimedia Software
---

### Post by sdowney717 on 2013-01-14
from over 2 hrs, to a little over an hour.

I made one change in kdenlive
vb=3000k
to
 -b 3500K -minrate 0K -maxrate 8000K

So why the big time difference?

And are these files vbr or constant?

---

### Post by malangaman on 2013-01-14
What version of Kdenlive are you using?
It looks like you are running it in Ubuntu? 12.04 or 12.10?
Was there nothing else running in background? How much RAM in the box?
I will attempt to replicate.

---

### Post by sdowney717 on 2013-01-14
kdenlive 0.9.2

Ubuntu 12.04 64 bit

The render args for the slower time are

```
f=mp4 hq=1 acodec=aac ab=%audiobitrate+'k' ar=48000 pix_fmt=yuv420p vcodec=libx264 minrate=0 vb=3000k g=250 bf=3 b_strategy=1 subcmp=2 cmp=2 coder=1 flags=+loop flags2=dct8x8 qmax=51 subq=7 qmin=10 qcomp=0.6 qdiff=4 trellis=1 aspect=%dar pass=%passes movflags=faststart
```

and
for faster time are

```
f=mp4 hq=1 acodec=aac ab=%audiobitrate+'k' ar=48000 pix_fmt=yuv420p vcodec=libx264 minrate=0 -b 3500K -minrate 0K -maxrate 8000K g=250 bf=3 b_strategy=1 subcmp=2 cmp=2 coder=1 flags=+loop flags2=dct8x8 qmax=51 subq=7 qmin=10 qcomp=0.6 qdiff=4 trellis=1 aspect=%dar pass=%passes movflags=faststart
```


I also have about 15 chrome tabs open and nautilus and kino

---

### Post by sdowney717 on 2013-01-14
I have also found the flag -crf 23 
[https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide)

So I set up args like this

```
f=mp4 hq=1 acodec=aac ab=%audiobitrate+'k' ar=48000 pix_fmt=yuv420p vcodec=libx264 -crf 23 g=250 bf=3 b_strategy=1 subcmp=2 cmp=2 coder=1 flags=+loop flags2=dct8x8 qmax=51 subq=7 qmin=10 qcomp=0.6 qdiff=4 trellis=1 aspect=%dar pass=%passes movflags=faststart
```

which also ran faster. with crf 23, final rendered file size went from 1.6gb to 1.0gb

---

