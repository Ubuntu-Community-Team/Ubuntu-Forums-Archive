---
title: "Convert video to Mp3"
date: 2018-06-18
forum: Multimedia Software
---

### Post by viktorbetter on 2018-06-18
[FONT=Arial]normal software for converting mshvushch in mp 3 for ubuntu not. I've been looking for ways to solve this problem. I found this application.[https://flvconverter.net/](https://flvconverter.net/) works simply. long do not need to understand. if u have options, better application than advise please)[/FONT]

---

### Post by TheFu on 2018-06-18
This doesn't work?
```
$ ffmpeg -i input-file.whatever output.mp3
```

Any video file (or audio file) input that ffmpeg understands will be converted to an audio-only MP3 file.  There are other options to control quality, sampling, etc., but that is the basic command.

---

