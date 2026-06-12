---
title: "FFmpeg TV capture issues"
date: 2009-10-01
forum: Multimedia Software
---

### Post by superoven on 2009-10-01
I'm using a Dazzle DVC100 capture card to record the input from my tv onto ubuntu. I have tried using mencoder to capture the input. It works, but it drops frames unacceptably often. 

So, I switched over to FFmpeg, which records the video much much better than mencoder did, however, I can't get it to record the audio too. This is the command that I'm using:

ffmpeg -f oss -i /dev/dsp1 -f video4linux2 -s 1280x960 -r 30 -i /dev/video1 -qscale 1 -acodec libmp3lame -ab 224k outfile.avi

Which looks perfect, but doesn't have any sound (I can confirm that /dev/dsp1 is my audio input from the tv). I used /dev/dsp just for kicks (my microphone) and it works, but this, obviously, is not what I intended.

So my question is, what can I do to get ffmpeg to read properly from /dev/dsp1 from a dazzle DVC100?

---

### Post by pigphish on 2009-10-05
I have the same unit. It registers as 
/dev/video0 and /dev/vbi0

I was able to succesfully use vlc to stream and live capture from the device. VLC used /dev/video0

---

