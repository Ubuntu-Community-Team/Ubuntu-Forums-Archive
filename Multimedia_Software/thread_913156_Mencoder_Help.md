---
title: "Mencoder Help"
date: 2008-09-07
forum: Multimedia Software
---

### Post by FlamingChainsaws on 2008-09-07
I have two problems with Mencoder. One, I can't convert swf files. Two, I use a Creative Zen Vision:M, and when I convert flv videos for it, the sound is strange. It sounds like harsh electronic static. I'm using this for converting:
```
mencoder file1.flv -o test1.avi -vf scale=320:240 -oac mp3lame -ovc xvid -xvidencopts bitrate=800
```
It's weird, because other file types usually work. Is there something I'm doing wrong?

---

### Post by eye208 on 2008-09-07
SWF (Shockwave Flash) is not a video format. There may be video clips embedded in it, but you have to extract them first before feeding them into MEncoder.

---

### Post by FlamingChainsaws on 2008-09-09
How do I extract the video from swf?

---

