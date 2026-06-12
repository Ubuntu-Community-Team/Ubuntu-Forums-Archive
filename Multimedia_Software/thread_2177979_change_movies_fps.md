---
title: "change movies fps"
date: 2013-10-01
forum: Multimedia Software
---

### Post by abandersnatch on 2013-10-01
I wish to change a films FPS from 30 to 10. How is this possible?

---

### Post by abandersnatch on 2013-10-01
try WinFF, we'll see how it turns out

---

### Post by lukeiamyourfather on 2013-10-01
Yes, you'll need a video encoder like Libav's avconv or FFmpeg. Both allow the output video FPS to be specified manually.

---

### Post by FakeOutdoorsman on 2013-10-01
Using ffmpeg:
```
ffmpeg -i input -r 10 -codec:a copy output
```
or with the [fps video filter](http://ffmpeg.org/ffmpeg-filters.html#fps):
```
ffmpeg -i input -vf fps=10 -codec:a copy output
```
Note that ffmpeg will simply drop frames to reach your desired output frame rate. I added "-codec:a copy" to [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) the audio instead of re-encoding.

You can download a recent [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds), or you can [compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

---

