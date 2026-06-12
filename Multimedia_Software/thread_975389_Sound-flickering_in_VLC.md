---
title: "Sound-flickering in VLC"
date: 2008-11-08
forum: Multimedia Software
---

### Post by Rakanishu on 2008-11-08
I tried to view an .avi file, but it didn't work with Totem so I installed VLC.

While it works, the sound is really terrible. Every 3-4 seconds there is a "click".

This happens with all .avi movies I play. It doesn't happen with flash movies or when listening to music.

What's wrong and how can I solve this?

Thanks

---

### Post by Rakanishu on 2008-11-08
Bump, cause it's one second page.

---

### Post by Rakanishu on 2008-11-08
Another bump, because of second page.

---

### Post by Rakanishu on 2008-11-08
Bump.

---

### Post by Bödvar on 2008-11-08
> **Rakanishu said:**
> Bump.
I'm guessing you have a codec problem. Try installing some codecs. I have had a similar problem, only the clicks were more like every 0,001 ms, i.e. there was great disturbance in the soundtrack of certain .avi files. My solution was to install a codec pack, which didn't work, but as it came with Media Player Classic, I tried playing the files using that program, and it worked perfectly. That was on Windows however.

My guess is that you are having a similar problem - find some codecs that are missing.

---

### Post by Rakanishu on 2008-11-08
Thanks for your answer.
Any idea what codecs this might be? Because I don't know what to look for...

---

### Post by Bödvar on 2008-11-09
> **Rakanishu said:**
> Thanks for your answer.
Any idea what codecs this might be? Because I don't know what to look for...

I haven't the faintest idea. My approach would be to just install a bunch of random codecs and see if the videos will play. Have you tried playing the videos in a player other than VLC?

---

### Post by thomasyen on 2008-11-09
Try Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) . It contains a repository of restricted codecs (including ones for AVI). Just follow the instructions on adding the repository, and I think you'll solve your problem.

---

### Post by Rakanishu on 2008-11-09
Thanks for your answer too.
That doesn't work either though. Maybe I have too many different codecs installed?

Every video player seems to have a problem. VLC has the sound glitch, Totem lags and flickers with the picture in fullscreen, Mplayer has: "error opening the video-out device". And Gxine has the same problem as Totem.

---

### Post by thomasyen on 2008-11-12
Have you installed the FFmpeg plugins for Gstreamer? It's supposed to natively support playback of AVI files.

---

### Post by Slowjoe on 2010-01-22
I tried the FFmpeg suggestion and it seemed to have solved my VLC intermittent sound glitch problem too - except it didn't.

I allready had the FFmpeg plugin for Gstreamer installed, i.e., gstreamer0.10-ffmpeg, but I didn't have ffmpeg itself.  Installing this also installed two lib files as dependencies. After trying this, the problem seemed to go away, and then came back.  Movie Player doesn't have this problem.   I like the VLC interface better however.  It seems a more powerful program.

If the movie is there, but the sound is glitchy, could this really be the wrong codec?

---

