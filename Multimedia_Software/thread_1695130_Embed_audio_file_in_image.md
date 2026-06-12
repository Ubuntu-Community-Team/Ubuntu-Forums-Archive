---
title: "Embed audio file in image"
date: 2011-02-25
forum: Multimedia Software
---

### Post by kommunisti on 2011-02-25
Is it possible to embed audio file to an image in ubuntu?

It's possible in Windows 7, when saving just the image from an imagechan.

---

### Post by FakeOutdoorsman on 2011-02-25
I don't understand what you mean. A movie of one image with an audio track? You can do that with FFmpeg:
```
ffmpeg -loop_input -i input.png -acodec copy -qscale 3 -shortest output.mkv
```

---

