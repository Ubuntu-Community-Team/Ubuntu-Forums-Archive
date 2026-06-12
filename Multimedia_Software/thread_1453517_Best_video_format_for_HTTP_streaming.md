---
title: "Best video format for HTTP streaming"
date: 2010-04-13
forum: Multimedia Software
---

### Post by PaulM1985 on 2010-04-13
Hi

I have created a server/client system for my home network to stream videos from my PC to a computer plugged into my TV.  I am using GStreamer as the core for the video playback on the client and I am using Apache WebServer for the source on the server which GStreamer on the client uses to play the videos.

I have noticed that the .avi files I have been testing can occationally get quite choppy and sometimes the audio gets out of sync.

Is there a particular file type which works best for this sort of task?

Paul

---

### Post by Maheriano on 2010-04-13
Look into HTML5, Youtube is switching over to it from Flash.

---

### Post by PaulM1985 on 2010-04-13
The way I am working currently is by having the client open and play:
[http://MY_IP_ADDRESS:PORT/VIDEOPATH/someVideo.avi](http://MY_IP_ADDRESS:PORT/VIDEOPATH/someVideo.avi)

where the address and port is for my desktop PC.

I was wondering if there was anything better than .avi for video streaming?  Maybe something that requires less processing or something...

Paul

---

### Post by LuridCinema on 2010-04-13
mp4 w/ h.264 compression would be great.  . you can convert w/ ffmpeg once you have the libraries installed

---

### Post by PaulM1985 on 2010-04-13
> **LuridCinema said:**
> mp4 w/ h.264 compression would be great.  . you can convert w/ ffmpeg once you have the libraries installed

Sorry if this is a really obvious question... What does h.264 mean?  I don't know too much (hardly anything) about video conversion.

EDIT:  Found out what it means.  Ignore this.

---

### Post by PaulM1985 on 2010-04-14
I have converted an avi to mp4 using WinFF and when trying to stream this I am getting a GStreamer general streaming error.  I also tried this on Totem to make sure that it wasn't just my program and Totem produces the same error when using "Open Location".  

Is GStreamer unable to stream mp4?

If so, any other suggestions for video format?

Paul

---

### Post by PaulM1985 on 2010-04-14
After testing Xine, it seems that this is much more capable for playing streamed media via http than GStreamer.

I will build the Xine lib into my client and take GStreamer out.

Paul

---

