---
title: "ffmpeg/avconv crashes when video frame isn't expected size"
date: 2012-10-12
forum: Multimedia Software
---

### Post by Skerit on 2012-10-12
I'm capturing my webcam using ffmpeg/avconv, but I keep running into this problem:

The v4l2 frame is 828212 bytes, but 829440 bytes are expected

And then it crashes. It should just skip that frame, not crash the entire application.

Does anyone have any ideas on how to make it work? Or maybe some other encoder which is able to stream

---

