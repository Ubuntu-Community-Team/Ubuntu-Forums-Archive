---
title: "jpg + mp3 = video"
date: 2011-12-11
forum: Multimedia Software
---

### Post by jasonlfunk on 2011-12-11
Hello. I have a group of mp3s and associated jpgs and want to create a video of them. My first attempt was close but it didn't work. This is what I tried.
```

ffmpeg -i 1.jpg -i 1.mp3 1.mp4
ffmpeg -i 2.jpg -i 2.mp3 2.mp4
ffmpeg -i 3.jpg -i 3.mp3 3.mp4
MP4Box -cat 1.mp4 -cat 2.mp4 -cat 3.mp4 -new full.mp4

```

This almost works except each of the images shows at the beginning for 1 sec each instead of changing at the mp3 boundaries. I'm not sure how to fix it. Any tips?

---

### Post by FakeOutdoorsman on 2011-12-12
**1. Create segments** (using current FFmpeg syntax):
```

ffmpeg -loop 1 -i 1.jpg -i 1.mp3 -shortest -c:v mpeg2video -qscale 1 -c:a copy -y 1.mpg
ffmpeg -loop 1 -i 2.jpg -i 2.mp3 -shortest -c:v mpeg2video -qscale 1 -c:a copy -y 2.mpg
ffmpeg -loop 1 -i 3.jpg -i 3.mp3 -shortest -c:v mpeg2video -qscale 1 -c:a copy -y 3.mpg

```
Depending on your FFmpeg version you may need to change:
[list]
[*]-loop 1 = -loop_input
[*]-c:v = -vcodec
[*]-c:a copy = -acodec copy
[/list]
**2. Combine files:**
```
cat 1.mpg 2.mpg 3.mpg > full.mpg
```
or
```
ffmpeg -i concat:'1.mpg|2.mpg|3.mpg' -c copy full.mpg
```
or re-encode to another format:
```
ffmpeg -i concat:'1.mpg|2.mpg|3.mpg' -c:v libx264 -preset slow -crf 24 -c:a libfaac -aq 100 full.mp4
```
Once again, Depending on your FFmpeg version you may need to change:
[list]
[*]-c copy = -vcodec copy -acodec copy
[*]-c:v = -vcodec
[*]-preset = -vpre
[*]-c:a = -acodec
[/list]
...and ffmpeg from repo may not support the *concat* protocol, but the *cat* command as shown should basically do the same thing.

---

### Post by satanselbow on 2011-12-12
... or cheat and do it in openshot...

---

### Post by jasonlfunk on 2011-12-12
Awesome. Thanks. I'll try it out later tonight.

---

