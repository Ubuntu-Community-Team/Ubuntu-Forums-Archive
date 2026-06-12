---
title: "Devede .iso gets area limitation in DVD player"
date: 2024-07-16
forum: Multimedia Software
---

### Post by opmartin2 on 2024-07-16
I got the same region error message and found I had to re-transcode the video files into a main/420 format before putting them into devede.  Like this:
  ```
ffmpeg -i input.mp4 -profile:v main -pix_fmt yuv420p output.mp4
```
Then it worked (NTSC).

---

