---
title: "Extract video part using mencoder"
date: 2009-04-08
forum: Multimedia Software
---

### Post by Epithemeus on 2009-04-08
Hi All,

I am trying to extract specific parts of a video (MPG format) using MEncoder.

1.	Upon using:
mencoder inputFile.mpg –ss 0.0 -endpos 600.0 -ovc copy -oac copy -o outputPart1.mpg

This allows me to extract the first 600 seconds of the video.

2.	To extract the next 600 seconds, I use the following:
                mencoder inputFile.mpg –ss 600.0 -endpos 600.0 -ovc copy -oac copy -o outputPart2.mpg

For some reason, this only yields the last 200 seconds (approx.) of the video. 


Am I missing something here? Any ideas would be very helpful!

Thanks!



epithemeus

---

### Post by justsomedude on 2009-04-08
You can only extract excerpts from a video without reencoding starting with a keyframe.

My guess would be your video contains very few keyframes.

So, either reencode while extracting excerpts or use a program like Avidemux to find keyframes so you can decide where to cut.

---

