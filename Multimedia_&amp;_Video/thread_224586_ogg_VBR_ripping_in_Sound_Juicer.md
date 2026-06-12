---
title: "ogg VBR ripping in Sound Juicer"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by aweller on 2006-07-28
Dear all,

I am used to ripping my CDs with Grip. With this I pass an encoding 'bitrate' of '3' (ie, an ogg quality value of 3). How does this work in Sound Juicer? I can see that for the 'CD Quality, Lossy' option the GStreamer pipeline is:

audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux

My guess is that this actually means a quality of '5'?! If I want to use '3', do I change the line above to read:

audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.3 ! oggmux

Thanks, Andy

---

