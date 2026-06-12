---
title: "How to convert Youtube FLV videos to AVI or other DVD format..."
date: 2009-03-18
forum: Multimedia Software
---

### Post by x C0MMAND0 x on 2009-03-18
*topic*

---

### Post by x C0MMAND0 x on 2009-03-23
Bump...I tried ffmpeg and it did not work.

---

### Post by Chemical Imbalance on 2009-03-23
This works great for me:
[http://media-convert.com/](http://media-convert.com/)

Another option is avidemux:

> sudo apt-get install avidemux

---

### Post by SuperSonic4 on 2009-03-23
Elltube: [http://www.kde-apps.org/content/show.php/Elltube?content=89693](http://www.kde-apps.org/content/show.php/Elltube?content=89693)

---

### Post by andrew.46 on 2009-03-24
Hi x COMMANDO x,

> **x C0MMAND0 x said:**
> Bump...I tried ffmpeg and it did not work.

FFmpeg is probably the best tool for this job so I suspect it could be *possibly* be the user rather than the tool at fault :-). If you are keen on exploring this further you could try the following

1. Pick up the latest FFmpeg by following the [FakeOutdoorsman's excellent guide]("http://ubuntuforums.org/showthread.php?t=786095").

2. Install youtube-dl from the Ubuntu repository.

3. Download a test flv from youtube as follows:

```
youtube-dl http://www.youtube.com/watch?v=4pIeFBs5HVQ
```

4. Examine the file with your brand new FFmpeg:

```
ffmpeg -i 4pIeFBs5HVQ.flv
```

and you will see the following:

```

    Stream #0.0: Video: flv, yuv420p, 320x240, 341 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s

```

5. Now if you *really* want the old avi format and perhaps mpeg4 video you can try the following:

```
ffmpeg -i 4pIeFBs5HVQ.flv -vcodec mpeg4 -sameq -acodec copy vampire.avi
```

And there you have quite a reasonable transcoded youtube video, it certainly looks ok on my computer anyway. Have a go at it, the youtube video is a real link.

All the best,

Andrew

---

### Post by FavouriteMilk on 2009-04-09
there's a great number of various convertors.
z.B. Flash to Video Encoder by Geovid - a nice program.

---

### Post by xc3RnbFO8P on 2009-04-09
**Devede** Add/Remove (all available application)

---

### Post by binbash on 2009-04-09
you can also try pytube

---

