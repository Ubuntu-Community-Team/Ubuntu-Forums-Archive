---
title: "FFmpeg/mencoder video loop?"
date: 2010-06-05
forum: Multimedia Software
---

### Post by dragos240 on 2010-06-05
How do you loop a video a number of times in ffmpeg or mencoder? I made a ogv out of a gif. It loops 1 time, so it's less than a second.

---

### Post by dragos240 on 2010-06-06
Bump.

---

### Post by FakeOutdoorsman on 2010-06-07
Some formats allow the use of *-loop_output 0* in FFmpeg which will loop infinitely.  I'm not sure which formats this can be used with.  You could also try looping with the player itself, such as MPlayer:
```
mplayer -loop 0 output.ogv
```
A third option is to make several copies of your input and feed that to FFmpeg, but it wouldn't loop infinitely.

---

### Post by xzero1 on 2010-06-07
This thread should help: [http://ubuntuforums.org/showthread.php?p=9417293#post9417293]("http://ubuntuforums.org/showthread.php?p=9417293#post9417293")

---

### Post by garry15 on 2010-11-08
I think this code will be helpful mplayer -loop 0 output.ogv

---

