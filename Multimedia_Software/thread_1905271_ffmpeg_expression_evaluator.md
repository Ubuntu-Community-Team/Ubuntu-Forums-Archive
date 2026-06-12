---
title: "ffmpeg: expression evaluator"
date: 2012-01-06
forum: Multimedia Software
---

### Post by danick on 2012-01-06
Hi,

I'm using ffmpeg to produce a video from a series of still images like this:

ffmpeg -f image2 -r 25 -i IMG%03d.jpg -vcodec h263p -r 25  vid.avi

The first '-r 25' determines how many images are progressed to create one second of video, the second '-r 25' is the framerate of the video (vid.avi). So if I want the succession of the images to be faster (e.g. double speed) but keeping the framerate at 25 fps I use e.g.:

ffmpeg -f image2 -r 50 -i IMG%03d.jpg -vcodec h263p -r 25  vid.avi

That works fine, so far. What I'd like to do now, is to change the number of progressed images per second of video continuously from, say 50 to 25, within the video, i.e. the video is at fast speed (50 images per second) in the begining and at normal speed (25 images per second) in the end of the video. Symbolically, I want something like

ffmpeg -f image2 -r 50:25 -i IMG%03d.jpg -vcodec h263p -r 25  vid.avi

My idea is, to solve that with the expression evaluation of ffmpeg and use the current frame as a variable to determine an integer between 50 and 25. But I have trouble to understand how I can access the number of current frame and write a proper function instead of 50:25 above, that ffmpeg understands. I could not find any example how to use the expression evaluation of ffmpeg, maybe one of you guys have experience with it and help me to get started? Thanks in advance!

---

