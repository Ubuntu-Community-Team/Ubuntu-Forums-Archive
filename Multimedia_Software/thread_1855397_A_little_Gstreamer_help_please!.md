---
title: "A little Gstreamer help please!"
date: 2011-10-06
forum: Multimedia Software
---

### Post by ammyt on 2011-10-06
Hey, i've been searching all over the interbet for the past 3 hours, trying to find a way to record audio + video, but nothing works! Can somebody give me a command?

It should be like:
gst-launch-0.10 -v v4l2camsrc device=/dev/video0 ! video/x-raw-yuv,width=1280, height=720 ! pulsesrc ! dspmp4venc ! avimux ! filesink location=/home/user/MyDocs/test.avi

but this or other patterns/encoders always get WARNING: erroneous pipeline: could not link v4l2camsrc0 to pulsesrc0

Help!

---

### Post by ammyt on 2011-10-06
Not a single reply?
WTF?

---

### Post by no2498 on 2011-10-07
see if guvcview  can find your cam & mic

---

