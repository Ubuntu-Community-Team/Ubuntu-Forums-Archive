---
title: "[SOLVED] Choppy 1080p HD playback?"
date: 2008-08-12
forum: Multimedia Software
---

### Post by kamitsukai on 2008-08-12
I'm trying to play back an 1080p HD video on my ubuntu PC but I'm getting choppy playback and some error in Mplayer telling me that I have to many of something in the frame buffer? I'm assuming that this is because my graphics card isn't powerful enough but can someone confirm that for me before I go out and buy a Geforce 7300GT

My current graphics card is an integrated Nvidia Geforce 7050

Thanks in advance:KS

---

### Post by cor2y on 2008-08-12
Its less to do with the GPU and more with the CPU.
Whats the max res of your monitor and your CPU clock speed?
Hidef video playback in linux requires that you have a powerful cpu any thing thats over 2ghz and dual core (720p video) or 2.6ghz Dual core or greater (1080p video), 128mb video memory and 1gb of ram.
Easiest way to avoid slow down of hidef media playback if you don't meet the specs is to either transcode to a less cpu intensive codec like say mpeg4 by reducing the video bitrate by half example 8mbit video down to 4mbit and the resolution if your monitor is too small example if all your monitor does is 1280x1040 at max settings then reduce the video to 720p (1280x720) when transcoding.Or you can edt the resolution mplayer displays if is too big for your screen or you want to avoid the packet error.
```
mplayer -xy 1280 foo.wmv
``` this will set the file to 720p resolution if its still choppy try reducing to -xy 720 (dvd resolution) and see how playback is then.

---

### Post by kamitsukai on 2008-08-12
well then I have more than enough: 4.2ghz dualcore cpu and 2gig's of ram and brand new dell hdmi monitor and the video codec is x264

---

### Post by cor2y on 2008-08-12
Its your onboard graphics gpu, it doesn't support hidef playback in windows or linux , sorry to say.

---

### Post by kamitsukai on 2008-08-12
oh right...looks like I'm buying a new graphucs card :)

thanks

---

