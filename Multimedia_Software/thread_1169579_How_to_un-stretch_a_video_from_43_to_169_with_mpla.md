---
title: "How to un-stretch a video from 4:3 to 16:9 with mplayer?"
date: 2009-05-25
forum: Multimedia Software
---

### Post by richterlevania3 on 2009-05-25
Hi there,

Let me explain: I´m using xwinwrap to make a video run as a wallpaper (wallvideo?). I´m trying to use a video with 16:9 aspect ratio, with those black bands. But, mplayer through xwinwrap is stretching the video to 4:3 format, so the video gets thin and ugly. I played with many options of mplayer, but to no avail. Is there some way to un-stretch the video and make the black bands appear again? Could somewhere help me out with this?

Thx in advance.

---

### Post by xzero1 on 2009-05-25
I'll give it a shot. It seems like the video is only being stretched vertically. What you might try is get mplayer to stretch it horizontally (decode it to your max horizontal video resolution before xwinwrap gets to stretch it.

mplayer -x horz

---

