---
title: "Simplistic analog television recording"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by SeanTater on 2008-01-27
I've been using ffmpeg to record analog TV shows from my TV tuner.

Altogether, the video and the audio are both fine. (Not perfect, but that can be addressed later). The problem is the sync between them.

The audio continually drifts backward. It's on average 1 second late per hour, and on occasion can be up to three. I've tried to reduce any programs that might be hogging the scheduler, and I've given ffmpeg root privileges and -20 niceness, but the a/v sync still isn't better. I've used -async and even -copyts on ffmpeg, but I still have no luck.

I don't mind changing programs or trying new options. Most of my attempts to fix it have been a shot in the dark. I haven't really tried mythtv or freevo because I don't think I need a whole framework for an occasional recording. Is there anything simple I can try?

---

### Post by yabbadabbadont on 2008-01-28
You might try mencoder.  I'm afraid that I don't know the correct syntax for what you are trying, but it is an alternative to ffmpeg.

---

### Post by SeanTater on 2008-01-28
I tried transcode, but I have not yet tried mencoder -- while I'm at it, any other suggestions?

---

