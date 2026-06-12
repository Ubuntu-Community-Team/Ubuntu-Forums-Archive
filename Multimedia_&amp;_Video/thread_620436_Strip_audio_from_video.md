---
title: "Strip audio from video"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by peterbrewer on 2007-11-22
I have a video which was taken at a youth weekend away.  I need to stip the audio so its just the pictures as there is some 'inappropriate language'.

Can anyone give advice on the best way to do that.

---

### Post by ron999 on 2007-11-22
Hi
What sort of video is it? Is it a DVD? Is it a mpg file or an avi file or what?

---

### Post by talkingwires on 2008-06-07
Seven months later, and I'm trying to figure out how do the same thing....

---

### Post by talkingwires on 2008-06-07
Well, I spent the past hour scouring Google, but not having much luck. Both mencoder and ffmpeg want to re-encode the video, which is just silly. I finally stumbled across a solution: avidemux. Just change the audio source from "video" to "none" and save the file. No re-encoding, just a video stripped of audio!

---

### Post by logos34 on 2008-06-07
> **peterbrewer said:**
> I have a video which was taken at a youth weekend away.  I need to stip the audio so its just the pictures as there is some 'inappropriate language'.

talk about 'parental discretion advised' -- for the PARENTS! :lolflag:

---

