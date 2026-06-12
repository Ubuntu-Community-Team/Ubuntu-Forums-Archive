---
title: "To play H.264 files"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by soongwoo on 2006-06-22
I'm using MPlayer to play DVD and other media files.
MPlaye is fine and sound is great.

Few weeks ago, when a H.264 file was played, I got an error
message like "too many packets in the buffer ..."
From that point, video is fine but sound is NOT.

Is there anyone to get similar experience with H.264 files?
Or is there anyone to resolve sound probem in MPlayer
when H.264 file is playing?

Thanks
soongwoo

---

### Post by Agent86 on 2006-06-22
Are you using mplayer from the command line? I've found that the command line version sometimes smoothly plays x264/h264 files that the GUI version stutters on. You could also try ```
mplayer -framedrop nameof.avi
```although this might cause unacceptable skipping.

---

