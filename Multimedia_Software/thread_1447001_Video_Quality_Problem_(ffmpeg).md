---
title: "Video Quality Problem (ffmpeg)"
date: 2010-04-04
forum: Multimedia Software
---

### Post by nccanderson on 2010-04-04
Hi,

I have two video files that I need to make the exact same quality. Both were recorded from a webcam (logitec webcam pro 9000), but one was recorded with a high resolution and low frame rate, while the other was recorded with a low resolution and high frame rate. 

I have tried reducing the resolution of the high res video (as they also both need to be the same size) but it still looks like it has a higher quality. I have also tried reducing the bitrate of the high res video but it becomes pixelated and I can't seem to match the bitrate of the low res video. What I need is for them to both look the same and a way to say that objectively, they have the same quality. I have tried playing with various ffmpeg commands but am not exactly sure what I need to do. Any help would be greatly appreciated!

ffmpeg output for both files: 

High resolution video:
Input #0, mpeg, from '216c15.mpg':
  Duration: 00:00:01.54, start: 0.500000, bitrate: 4996 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 960x720 [PAR 1:1 DAR 4:3], 104857 kb/s, 30 tbr, 90k tbn, 30 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s

Low resolution video:
Input #0, mpeg, from '216c30.mpg':
  Duration: 00:00:01.86, start: 0.500000, bitrate: 3291 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 104857 kb/s, 30 tbr, 90k tbn, 30 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, s16, 64 kb/s

---

### Post by LuridCinema on 2010-04-04
What resolution do you ultimately want ?
try the below if you have the libraries installed for h.264

```

ffmpeg -i INPUT.mpg -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -wpredp 0 -s 640x480 -r 30 -crf 24 -threads 0 OUTPUT.mp4

```The above would give you an mp4 file 640x480 at 30 frames per sec

---

### Post by nccanderson on 2010-04-04
Thanks for the quick reply! 

I want to drop the quality of the high res file down to the low res one. I've tried out your ffmpeg commands and came up with two mp4 files, however, the high res file still looks like a much higher quality video than the low res file (more clear, sharper). The problem is that I need to make sure that both video files are the same subjective quality because I'm using them to compare the effect of the frame rate on the perception of the videos. 

I'm thinking that maybe the -crf option might be the way to go, but I'm not sure. Any thoughts?

---

### Post by LuridCinema on 2010-04-04
You might drop the high res one into Cinelerra and add some blur to the good one and mebbe play w/ the contrast & colors etc to even them up... that is where the ART of editing comes in. Openshot might help too...
Good Luck

---

