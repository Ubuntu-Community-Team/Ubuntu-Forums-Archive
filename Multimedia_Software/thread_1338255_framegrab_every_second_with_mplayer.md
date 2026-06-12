---
title: "framegrab every second with mplayer"
date: 2009-11-26
forum: Multimedia Software
---

### Post by Orange Kingdom on 2009-11-26
Hi,

I want to framegrab every 1 second or 10 second of a videofile with mplayer.
Anyone knows the commandline?

---

### Post by Orange Kingdom on 2009-11-26
I found it with ffmpeg:

ffmpeg -i some.avi -an -r .1 -y test%d.jpg


The '-r' option specify the rate, in frames per second. In the above command the rate is '.1', so one frame grab is generated for each 10 seconds of video.

---

### Post by andrew.46 on 2009-11-26
Hi Orange,

> **Orange Kingdom said:**
> I want to framegrab every 1 second or 10 second of a videofile with mplayer.
Anyone knows the commandline?

I am not completely sure how to automate the task as you request but if you have a look at Tip no. 5 of the following guide:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

you will see how MPlayer generates screenshots and I am sure there must be a way to automatically generate the screenshots at a *set interval* but I will have to admit it defeats me at the moment :confused:.

All the best,

Andrew

---

