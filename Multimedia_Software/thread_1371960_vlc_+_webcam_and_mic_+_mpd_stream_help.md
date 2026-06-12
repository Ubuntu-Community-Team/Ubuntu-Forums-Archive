---
title: "vlc + webcam and mic + mpd stream help"
date: 2010-01-04
forum: Multimedia Software
---

### Post by brian183 on 2010-01-04
Hello,

I'm trying to setup a webcam stream using vlc and I'm essentially in working order but I want to take it a step further.  I was wondering if it's possible for vlc to stream a mpd stream along with the audio from my mic.  Essentially, I want vlc to mux the audio stream from my mic with the audio from mpd stream and stream that audio along with the webcam video. I've tried on my own but VLC is pretty intense and I'm sure I'm missing something I can try.

Another way I could maybe do it is with pulse audio.  Is it possible for pulse audio to mux the audio from the mic with the audio from the mpd stream into like a virtual input device? If so, what would I enter in vlc for the audio input and, of course, how?

Thanks for your help.

---

### Post by brian183 on 2010-01-05
bump.

So far I've tried making mpd output to FIFO and local http stream.  Then I try to attach either of them with --input-slave to my webcam and mic in vlc but my stream ends up being the mpd stream only with no video or mic audio.  Any help would be appreciated.

-brian

---

