---
title: "ogg from jpegs or m4v"
date: 2011-02-11
forum: Multimedia Software
---

### Post by adamSpline on 2011-02-11
Hi all,

I am looking for a way to create an ogg video file from a series of jpegs from the command line.  I have not come up with a good solution, any ideas?

Also, I can create an h,264 m4v from the jpegs, so perhaps someone knows a command line to get a h.264 into an ogg file.

many thanks,

-Adam

---

### Post by Chronon on 2011-02-11
ffmpeg should work.  Here's a similar topic except ending up in .mpg: [http://ubuntuforums.org/showthread.php?t=936409](http://ubuntuforums.org/showthread.php?t=936409)

Based on that, I would expect the following command to at least produce an ogg theora video from a set of images with numeric filenames.
```
ffmpeg -f image2 -i %d.jpg video.ogg
```

---

