---
title: "Gstreamer"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by Belak on 2007-12-29
gstreamer is being stupid.
One of my songs was encoded and my media player 9rhythmbox) thinks it's 2 times the length that it actually is.

Here's my pipeline: 
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc quality=0 mode=0 vbr=4 vbr-quality=0 vbr-min-bitrate=256 vbr-max-bitrate=320 ! xingmux ! id3v2mux

Any ideas?

Thanks,
Belak

---

