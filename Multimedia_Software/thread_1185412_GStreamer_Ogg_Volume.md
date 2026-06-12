---
title: "GStreamer Ogg Volume"
date: 2009-06-12
forum: Multimedia Software
---

### Post by Mad-Halfling on 2009-06-12
I am using sound juicer to rip CDs and am getting ogg files out ok.  Is there a way to change (increase) the volume on the created files?  I've found some threads on the gstreamer options but there doesn't appear to be a volume or gain option.  Here's the options I'm using ATM

audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.15 ! oggmux

Cheers 

MH

---

