---
title: "ffmpeg screen capture"
date: 2013-03-16
forum: Multimedia Software
---

### Post by 3dmatrix on 2013-03-16
For screen capture, Record my desktop does not works on my system for what ever reason so I use the following code :

    ffmpeg -f alsa -i hw:0,0 -acodec pcm_s16le -f x11grab -r 30 -s 720x474 -i :0.0+380,134 ~/out5.m4v

It captures the screen video but captures the sound from the speakers.

As i could not get any proper solution on this forum, i tried to capture the screen video with the speaker sound. Then split and delete that sound. Next i recorded the sound of that video by running it the second time and recording the sound by sound recorder application. Initially it was recording the sound from the speaker but when i changed the System Settings > Sound to Analog Stereo Output instead of Analog Stereo Duplex, the recorder could record sound directly from the sound card. And then finally i had to join the video and this new sound to get my final video. But some times it is not possible to run the video or record the screen activity 2 times. Even after making that change in the settings i could not use the above code to record the desired video with the sound from the sound card. Anyway this entire work is very time consuming. So can any one tell me , what changes should i do in the above code to be able to record sound directly from the sound card instead of the speaker, while recording the video ?

---

### Post by coldraven on 2013-03-16
This worked for me
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0  -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0  output.mkv
```

It came from here:
[http://ubuntuforums.org/showthread.php?t=1392026&p=8746719#post8746719](http://ubuntuforums.org/showthread.php?t=1392026&p=8746719#post8746719)

---

### Post by 3dmatrix on 2013-03-16
> **coldraven said:**
> This worked for me
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0  -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0  output.mkv
```

It came from here:
[http://ubuntuforums.org/showthread.php?t=1392026&p=8746719#post8746719](http://ubuntuforums.org/showthread.php?t=1392026&p=8746719#post8746719)

Sorry it gives the following error :

[matroska @ 0x973a8a0] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1 >= 1
av_interleaved_write_frame(): Invalid argument

---

### Post by mc4man on 2013-03-16
you can try - 
install pavucontrol
Start a ffmpeg recording, open pavucontrol (pulseaudio volume control), open recording tab & select Monitor of built-in ..
Then close pavucontrol. (and exit your recording.
From then on the 'Monitor of..' should be auto-selected when running a ffmpeg screen cap command

---

