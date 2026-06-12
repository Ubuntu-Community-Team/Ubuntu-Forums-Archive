---
title: "Creating MJPEG stream with ffmpeg"
date: 2016-04-25
forum: Multimedia Software
---

### Post by Andrew_Wood on 2016-04-25
Is it possible to use the segmenter with ffmpeg to produce a live stream where the client always starts at the latest frame when they connect and older frames are automatically deleted?

Currently I can only get it to produce an ever growing file where the client always starts from the oldest frame


Im currently using this (where /usr/local/www/data is served up by lighttpd)
```
ffmpeg -i rtsp://192.168.111.1 -vcodec mjpeg -acodec copy /usr/local/www/data/stream1.mkv

```

Thanks

---

