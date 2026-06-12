---
title: "Help with playing Video"
date: 2007-08-05
forum: Multimedia &amp; Video
---

### Post by PropheticAngel on 2007-08-05
When I try to play a video in totem, the sound is way out of sync.
Mplayer says Error opening/initializing the selected video_out (-vo) device.
VLC has no sound at all.

I have had Ubuntu Feisty for about 4 days now. I put on pulse-audio to fix prior audio problems.

Section "Device"
Identifier "Generic Video Card"
Driver "fglrx"
Busid "PCI:1:0:0"

I have a radeon mobility x1400. This is on a T60.

UPDATE: I fixed it.  Removed g-streamer and put on xine.

---

