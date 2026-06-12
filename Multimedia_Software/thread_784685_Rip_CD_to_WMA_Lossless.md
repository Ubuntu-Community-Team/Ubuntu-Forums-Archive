---
title: "Rip CD to WMA Lossless?"
date: 2008-05-06
forum: Multimedia Software
---

### Post by eheyl on 2008-05-06
Hey all! I need to rip a CD to WMA Lossless compression. It is a meditation program called Holosync. I know that Sound Juicer does MP3 but its lossy. The support person I talked to was adament about lossless compression. Does anyone know how to do so? I'm in Hardy 8.04. Thanks!

---

### Post by fraureichlich on 2008-05-22
WMA lossless is basically a VBR WMA, WMA is normally lossy.
Not all that many DAPs will play WMA lossless. 
So if you are looking for good quality and portability, make a high quality MP3 profile in Sound Juicer.
Sound Juicer preferences, edit profiles, create new. Call it something and use the following in the gstreamer field, mark as active, restart Sound Juicer.
[B]
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=320 ! id3v2mux[/B]

Or FLAC is a lossless option but not many DAPs support it.

Either way you should still entrain your brain, check out a program called gnaural, it creates "delta" frequencies from two simple frequencies, like Holo-Sync does with music.

---

