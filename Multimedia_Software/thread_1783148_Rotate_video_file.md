---
title: "Rotate video file"
date: 2011-06-15
forum: Multimedia Software
---

### Post by Condor Cluster on 2011-06-15
Hi,
 
I have two video files taken with my phone, but unfortunately they are on their sides.
 
I was messing around with vlc, and found in the filters option menu, a setting to rotate the video 90 degrees, which is just what I was looking for.... BUT it won't let me save this (I guess you have to re-encode the whole file)
 
What is the easiest way to rotate video files (.3gp) and keep it in that state, without losing loads of quality?
 
Thanks.

---

### Post by ajgreeny on 2011-06-15
ffmpeg, mencoder, and some other apps will do it I think, but I suspect you will not get away without decoding then re-encoding.

---

### Post by FakeOutdoorsman on 2011-06-15
This can be done using FFmpeg, but you will have to re-encode as ajgreeny mentioned. See my example in [Re: [video editing] rotate video 90 degrees](http://ubuntuforums.org/showthread.php?p=10905703#post10905703). You may have to modify the example to get the format you want.

---

