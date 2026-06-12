---
title: "[CMD Line] Video to Photo Stitch"
date: 2016-01-01
forum: Multimedia Software
---

### Post by uMinded on 2016-01-01
I am looking for a piece of software that will let me convert a video into a photo stitched image via command line.

Preferable if it was accessible via a PPA and not source compile.

---

### Post by FakeOutdoorsman on 2016-01-01
What is a "photo stitched image"? Can you provide an example of the desired result?

---

### Post by uMinded on 2016-01-01
> **FakeOutdoorsman said:**
> What is a "photo stitched image"? Can you provide an example of the desired result?

Like a panorama from multiple images. Like [http://hugin.sourceforge.net/](http://hugin.sourceforge.net/) but it needs to be `video -> img` via comand line.

---

### Post by FakeOutdoorsman on 2016-01-01
```
ffmpeg -i input -filter_complex "scale=120:-1:flags=lanczos,tile=5x1:padding=5:margin=5" -frames:v 1 -q:v 3 tile.jpg
```

See docs on scale, tile, fps (to change intervals), select (for auto scene selection).

[https://ffmpeg.org/ffmpeg-filters.html](https://ffmpeg.org/ffmpeg-filters.html)

---

