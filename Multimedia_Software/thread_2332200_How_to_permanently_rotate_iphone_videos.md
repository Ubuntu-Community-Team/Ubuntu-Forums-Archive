---
title: "How to permanently rotate iphone videos"
date: 2016-07-29
forum: Multimedia Software
---

### Post by bojan2 on 2016-07-29
I have iphone4s video which i want to rotate and transcode.

vlc plays video correctly while on my windows machine, windows media player  and majority of other players does not rotate it.

I tried using ffmpeg:
```
ffmpeg -i input.mp4 -vf transpose=1 -strict -2  ouptut.mp4


```

According to [ffmpeg documentation]("https://ffmpeg.org/ffmpeg-filters.html#transpose") "transpose=1" should rotate my videos 90 degrees clockwise which is what i actually need but my video ends rotated by 180 degrees

To simplify:

My video: &#8592;
Expected: &#8593;
After transcoding: &#8594;

---

### Post by shantiq on 2016-07-30
hi bojan


if the syntax has not changed since 2011   here is [one way]("https://ubuntuforums.org/showthread.php?t=1775561&p=10905703#post10905703")

---

### Post by bojan2 on 2016-07-30
Well it looks like the problem was the rotation field in metadata, ffmpeg takes that into account when rotating. Result is rotation of 180 degrees.

Solution was to simply set rotation field to 0 and then re-encode video with command I first time tried

```
ffmpeg -i input.mp4 -c copy -metadata:s:v:0 rotate=0 -strict -2  output.mp4 // This sets rotation field to 0 in metadata
ffmpeg -i output.mp4 -vf transpose=1 -strict -2 final.mp4 // This rotates video by 90 degrees

```

I don't know is this possible with one command

---

### Post by FakeOutdoorsman on 2016-08-03
FFmpeg has for some time been able to automatically rotate video based on the rotate metadata:
```
ffmpeg -i input.mp4 -c:a copy output.mp4
```
No need for any filters or messing with metadata. If your ffmpeg does not do that then it is old, but you can [download an already compiled recent ffmpeg binary](http://johnvansickle.com/ffmpeg/) and use that instead.

---

