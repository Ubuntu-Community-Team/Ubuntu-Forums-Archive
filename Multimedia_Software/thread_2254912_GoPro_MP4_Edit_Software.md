---
title: "GoPro MP4 Edit Software??"
date: 2014-11-30
forum: Multimedia Software
---

### Post by mcman56 on 2014-11-30
I just purchased a gopro Hero 3+ silver but their software is not offered in a Linux version.  With the USB connector, I can view in "Videos" but would like something that can at least edit a video to cut out a specific portion.  Is anything like that available for Ubuntu?  Is there a way to get the gopro software working in Ubuntu?

---

### Post by tgalati4 on 2014-11-30
Take a look at *openshot*.

---

### Post by Bucky Ball on 2014-11-30
Kino is another possibility. If you want to get serious, Cinelerra.

---

### Post by FakeOutdoorsman on 2014-12-01
If you like cli use ffmpeg:
```
ffmpeg -ss 60 -c copy -t 00:03:00 output
```
[list]
[*]This will skip the first 60 seconds of the input and make an output that is 3 minutes long. Both **-ss** or **-t** can accept a value in seconds or hh:mm:ss.ms as shown in the example.
[*]Using **-c copy** will enable [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) mode, so it will simply re-mux instead of re-encode, thus preserving the quality and being a fast process.
[*]If you want to re-encode see: [FFmpeg H.264 Video Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264)
[*]Since FFmpeg development is so active (and because Ubuntu doesn't offer it until 15.04) you can get a build from the [download page](http://ffmpeg.org/download.html).
[/list]

---

