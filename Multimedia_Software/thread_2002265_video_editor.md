---
title: "video editor"
date: 2012-06-12
forum: Multimedia Software
---

### Post by Georgescu1 on 2012-06-12
i need a video editor that allows me to add a video in a video.
add a video file on top of another video file at what position i want and at what scale i want
something like Adobe after effects

edit:
I heard i can do it with ffmpeg but it's more complicated
basically i want video1 to be my main video and to it add video2 at a specific location in video1, and ofcourse i have to resize video2 first which is not really a problem

---

### Post by FakeOutdoorsman on 2012-06-12
You can do this with Kdenlive: [Picture in picture transition](http://www.kdenlive.org/tutorial/kdenlive-picture-picture-transition). It says "transition", but the video shows the basic method of making a PiP.

You can do this with ffmpeg too, but I don't have an example handy. See the documentation for the *[scale](http://ffmpeg.org/libavfilter.html#scale)* and *[overlay](http://ffmpeg.org/libavfilter.html#overlay-1)* filters (and the *-filter_complex* option if you're using a more recent ffmpeg).

---

