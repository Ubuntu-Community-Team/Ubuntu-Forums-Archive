---
title: "screencasting -- favorite method ?"
date: 2013-03-15
forum: Multimedia Software
---

### Post by mike acker on 2013-03-15
what's the favorite method of screen-casting ?

i'm working with Kazam right now
i think the "webm" format is a bit new ? and windows folks probably don't have a reader for it ?

mp4 should be better . i like the .avi container

---

### Post by FakeOutdoorsman on 2013-03-16
> **mike acker said:**
> what's the favorite method of screen-casting ?
I use this: [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

I haven't tried kazam.

[ffcast](https://github.com/lolilolicon/FFcast2) is worth looking at but you'll have to compile it. Basically the same as above, but has additional tools that allow easier selection of the window(s)/area that you want to record; such as using your mouse to draw a box of the area you want to record or simply clicking the windows that you want recorded. I'm not sure if it supports audio recording however, but you can probably tweak the script to allow it to do so.

> **mike acker said:**
> i think the "webm" format is a bit new ?
VP8 video (the usual video format used with webm container) will not give you the same quality/file size that you can get using x264 to encode H.264 video.

> **mike acker said:**
> windows folks probably don't have a reader for it ?
I'm not sure, but I will guess "no" unless they use VLC.

> **mike acker said:**
> mp4 should be better . i like the .avi container
mp4, like webm, is a container format that can contain various video formats and audio formats. avi container format is quite dated and there are few reasons to use it these days.

---

