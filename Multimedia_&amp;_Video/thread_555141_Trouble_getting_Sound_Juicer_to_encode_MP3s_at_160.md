---
title: "Trouble getting Sound Juicer to encode MP3s at 160KB/s"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by Noah0504 on 2007-09-19
For the life of me, I can't get Sound Juicer to encode MP3s at 160KB/s.  This is what I have for the Gstreamer pipeline:

> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=160 ! id3v2mux

---

