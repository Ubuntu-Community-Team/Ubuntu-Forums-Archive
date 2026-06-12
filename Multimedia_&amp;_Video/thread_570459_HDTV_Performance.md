---
title: "HDTV Performance?"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by somethingsin on 2007-10-08
I tried watching a 1920x1080 video clip today, but it was going so slowly it only refreshed every second or so, with lots of artifacting going on as well. This happened in both Movie Player and VLC
The same file under windows played quite smoothly in WMP, (but again not in VLC).
My Pentium M 2.0Ghz is just on the edge when it comes to this type of video. It can just about manage, at 100% cpu. Maybe my GPU isn't helping out in linux like it does in Windows..

Anyone have any tips for improving performance. I dislike the idea of having to boot into windows to watch HD movies

---

### Post by rsambuca on 2007-10-08
What format is the clip in?  What videocard do you have?  What video driver are you using?  How much RAM do you have?

---

### Post by somethingsin on 2007-10-08
> **rsambuca said:**
> What format is the clip in?  What videocard do you have?  What video driver are you using?  How much RAM do you have?



-It's a wmv (reported as WMV3 by VLC), so I guess that counts against it, but MPEG2 transport streams seem to have the same problem. Don't really have any other material to test it on atm.

- I have a GeForce Go 6800 ULTRA, an NV 42 core, I  think, though it might be a 41.

- using the nvidia proprietary driver that comes with gutsy.

-1GB ram, but it doesn't come close to filling up, if system monitor is to be believed

---

### Post by rsambuca on 2007-10-08
I haven't had very good playback with wmv files.  It is a closed source, proprietary format, so it won't work with linux as well as an open source format.

---

### Post by Ryan H on 2007-10-08
Your GPU does have some degree of Video acceleration in it. I'm not sure if VLC takes advantage of this, but I know Xine does. I have a 6600GT with an Athlon 64 at 2.45GHz, when I play 1080p content with Totem it does the same thing yours does, but with Xine it offloads a significant portion of the decoding process to the GPU and everything works perfectly.

-Ryan H

---

### Post by rsambuca on 2007-10-08
> **Ryan H said:**
> Your GPU does have some degree of Video acceleration in it. I'm not sure if VLC takes advantage of this, but I know Xine does. I have a 6600GT with an Athlon 64 at 2.45GHz, when I play 1080p content with Totem it does the same thing yours does, but with Xine it offloads a significant portion of the decoding process to the GPU and everything works perfectly.

-Ryan H

I'll have to try that.  You have virtually identical specs to me.

---

