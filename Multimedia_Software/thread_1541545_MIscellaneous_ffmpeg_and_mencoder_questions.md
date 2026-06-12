---
title: "MIscellaneous ffmpeg and mencoder questions"
date: 2010-07-29
forum: Multimedia Software
---

### Post by Kale Good on 2010-07-29
These are beginner questions, things that have come up as I learn about video production and the command line tools for it.

1.) Why does mencoder encode many, many, many times faster than ffmpeg? I thought it was using ffmpeg. (maybe it is just my machine).

2.) Why is mencoder able to have syncronized audio when recording from my webcam, but ffmpeg is not? 

Here are the respective commands:
mencoder:
mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi

ffmpeg:
ffmpeg -f oss -i /dev/audio1 -f video4linux2 -i /dev/video0 -vcodec mpeg4 -f h264 -s 480x360 -r 30 -acodec aac -f mp4 test3.mp4


3.) As a matter of fact, ffmpeg can never seem to synchronize audio. In fact, it is the reason I started learning mencoder. Why is this?

4.) Are -vsync and  -async  the (best) tools used for solving synchronization problems? What is a good value for -async?

Thanks,
Kale

---

