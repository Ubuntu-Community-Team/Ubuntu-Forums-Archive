---
title: "ctrl-c doesn't exit mencoder"
date: 2008-09-01
forum: Multimedia Software
---

### Post by josvanr on 2008-09-01
hi

i use mencoder to record movies from my webcam using this from the 
commandline:

```
mencoder tv:// -tv device=/dev/video1:driver=v4l2:gain=60:brightness=10:input=2:noaudio:width=640:height=480:fps=30:normid=0 -ovc lavc -lavcopts vbitrate=16000:vcodec=mpeg4 -o outputfile.avi
```

When I want to stop recording, I try to press ctrl-c, but then I see:

```
Pos:   2.7s     29f ( 0%)  7.99fps Trem:   0min   0mb  A-V:0.000 [1035:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1035.321 kbit/s  (129415 B/s)  size: 349421 bytes  2.700 secs  29 frames
```


which stays like this. The command prompt doesnt return. I have to 'kill -signal KILL mencoder' to really stop the program. Now this is fine for 
mpeg4 codec (the movie looks fine), but when I try the dvvideo codec
the output file is empty. Maybe this is due to the mencoder not exitting
properly. How do I properly exit mencoder started from the commandline?

josvanr

---

