---
title: "Can ffmpeg determine the time (length) of a video ?"
date: 2015-12-08
forum: Multimedia Software
---

### Post by oygle on 2015-12-08
Have a video that when it plays, the length/time does not show. Using VLC. Can I use ffmpeg to determine the time and then update the MP4 to contain the time/length ?

---

### Post by oygle on 2015-12-08
Length can be determined by ```
ffmpeg -i VideoClip2.mp4
```

Now to find out how to update the MP4 so that it contains(stores) the length/time ??

---

### Post by viewera on 2015-12-10
You could try to remux the video like this.

```
ffmpeg -i VideoClip2.mp4 -c copy NewClip2.mp4
```

---

