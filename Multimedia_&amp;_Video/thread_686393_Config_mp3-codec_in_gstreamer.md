---
title: "Config mp3-codec in gstreamer"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by Azyx on 2008-02-03
When I look at Sound-jucier -->preferens--> Output format edit profile- mp3  --> Gstreamer pipeline. it's says:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

When I look in the help is, says that if you want to use mp3, get plugin and edit like this:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux

My question is. What is vbr=0 and vbr-quality=6.

Cheers Azyx

---

