---
title: "codec id's what do they mean?"
date: 2012-03-22
forum: Multimedia Software
---

### Post by chickenPie4breakfast on 2012-03-22
Is there some list of what the numbers mean?
I was trying to rip the audio off a video using ffmpeg and got this message

Encoder (codec id 86017) not found for output stream #0.0

the video was in mp4 format- so I guess I need a codec but which one - what does 86017 mean!

I wonder if it's a lame codec needed? anyway I solved it by 

sudo apt-get install ffmpeg libavcodec-extra-52

now it encoded fine.  I am using Maverick

---

### Post by MirkoK on 2012-03-22
> **chickenPie4breakfast said:**
> Is there some list of what the numbers mean?
Encoder (codec id 86017) not found for output stream #0.0

the video was in mp4 format- so I guess I need a codec but which one - what does 86017 mean!


It's probably just an ffmpeg/libavcodec internal ID number, and I guess there's no other way to know what it means than to read the source code. However, I couldn't find the ID nor the exact message in the source I got with apt-get source on Lucid. Seems it has been change quite long ago:

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg799750.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg799750.html)

---

