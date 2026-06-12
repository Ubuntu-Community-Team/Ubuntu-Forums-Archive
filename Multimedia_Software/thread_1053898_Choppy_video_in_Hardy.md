---
title: "Choppy video in Hardy"
date: 2009-01-29
forum: Multimedia Software
---

### Post by themanofthehour on 2009-01-29
I'm having the same problem. No video program will play steady video (but it does seem a bit better when the mouse is idle). I doubt it's my equipment (i could be wrong though), it's all new, ati 4870, E8400 processor, ect. I've been scouring the forums but havent been able to find a solution that works and was wondering if anyone has found a solution yet. I'm relatively new to ubuntu so any help would be appreciated.

---

### Post by markbuntu on 2009-01-29
Which driver are you using and which version of Ubuntu?
The newest driver from ati, 8.12 has vast improvements in video playback over earlier versions.
Anyway, you can try System/Multimedia systems Selector/Video/Default Output/Plugin choose X Window System (No Xv). That will help with gstreamer apps.

But the easiest and most complete way to get rid of that problem for now is to just set desktop visual effects to none when you want to watch a video.

---

