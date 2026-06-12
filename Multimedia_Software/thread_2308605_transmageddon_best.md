---
title: "transmageddon best?"
date: 2016-01-04
forum: Multimedia Software
---

### Post by ubto66 on 2016-01-04
ubuntu 14.04 64bit

Is transmageddon the best gui video converter? Thanks.

---

### Post by Rob Sayer on 2016-01-04
I don't think so.  It's just another GUI for ffmpeg/avconv and nothing special.  What do you want to convert?  What is it going to be played on?

Video encoding is actually quite complicated.  There aren't any universal ideal encoder settings because every video is different.  There are some excellent, powerful encoders out there that are really only suited to video geeks who understand this stuff.  And there are a lot of easier ones that don't give you high quality results.  The best ones I know of as far as having a good balance between power and ease of use are Avidemux (better for divx/xvid output) and handbrake (which only outputs h.264, which is more standard nowdays).  Both are in the repos.

If you're new to video encoding the first thing you need to know is that you cannot reduce the file size significantly without losing quality.  Just how much quality loss is acceptable is up to you.

The second thing is never use 1 pass bit rate/file size (the 2 are the same thing really) encoding.  Many simple encoders just use that because it is the fastest way, but the quality *will* stink.

---

### Post by ubto66 on 2016-01-07
Thank you. Is is more about how I can set the size of the  output file. If a dvd movie backup is about 4gb, how do I convert it into about 1gb? 
I tried transmageddon ogg. The output quality was fine. The size of the file about 2gb. Two times the file size I wanted. Can ubuntu do converting into webm? Webm files seems to be of fine quality. Is webm free software?

---

### Post by Yellow Pasque on 2016-01-07
Handbrake

---

