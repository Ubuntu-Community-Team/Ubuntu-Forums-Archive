---
title: "Totem can't play videos with subtitle"
date: 2009-11-14
forum: Multimedia Software
---

### Post by ZuLuuuuuu on 2009-11-14
Hi,

I installed 9.10 yesterday. I have a problem with Totem not being able to play videos with subtitle. Whenever a video has a subtitle file (with the same name of the video and .srt or .sub extension) Totem just freezes.

I can play the same videos when I delete the subtitle file. And these are videos I was able to watch on 9.04 without a problem.

What might be the problem?

---

### Post by lovinglinux on 2009-11-14
I recommend [smplayer](apt:smplayer), which has an excellent subtitle support, including ssa.

---

### Post by zwaardmeester on 2009-11-16
This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/441396"). A workaround could be to rename the subtitle file to something different then the video, and subsequently load the subtitle file manually though the menu "View".

---

### Post by ZuLuuuuuu on 2009-11-16
> **zwaardmeester said:**
> This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/441396"). A workaround could be to rename the subtitle file to something different then the video, and subsequently load the subtitle file manually though the menu "View".

Thank you very much...

---

