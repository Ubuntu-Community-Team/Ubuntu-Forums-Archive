---
title: "Video Editors"
date: 2013-11-06
forum: Multimedia Software
---

### Post by wayne5 on 2013-11-06
Can anyone suggest a video editing software for Ubuntu 12.04 that will allow me to remove a weather update banner from the bottom of TV recordings? :popcorn:

---

### Post by TheFu on 2013-11-06
avidemux, but ffmpeg, mencoder and others will do it too, though without the nice GUI that avidemux has.  Regardless, this will require transcoding the video - it isn't like a file copy or replacing a "container."

handbrake can do it too ... provided you do not need to edit more than just the cropping.  "cropping" is the term you need.

---

### Post by Rob Sayer on 2013-11-09
Unfortunately cropping is probably the most reasonable way to do this, but I suspect the OP wants to just take it off the original video.  I've seen that question asked on multimedia forums often.

People new to digital video often think that they can do something like that straightforwardly with no re encoding.  You can't.  There's absolutely no video under that text.  It's not an extra layer like a .srt subtitle file.  Even with stationary text/watermarks it's not really worth the effort.

---

