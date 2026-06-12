---
title: "FFMPEG mpeg2 metadata"
date: 2012-01-24
forum: Multimedia Software
---

### Post by Vontux on 2012-01-24
Hello, I was wondering if there is a way to use ffmpeg to set the metadata for mpeg2 files? Would it be possible do something like what is answered here:
[http://ubuntuforums.org/showthread.php?t=1193808]("http://ubuntuforums.org/showthread.php?t=1193808")

---

### Post by FakeOutdoorsman on 2012-01-24
I doubt .mpg or .mpeg support metadata. Alternatively you could copy the video into another media container format that does.

```
ffmpeg -i input.mpg -vcodec copy -acodec copy -metadata title="Cheese Eating Contest" -metadata  artist="Vontux" output.mkv
```

---

