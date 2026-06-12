---
title: "Jerky video"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by clk99 on 2007-06-12
On my new Feisty installation I'm getting jerky video when playing divx AVIs.  This happens in both MPlayer and VLC.  I haven't tried viewing any other video format so I can't say for sure that it is just divx videos.  It's not a problem with the files themselves because they play fine in VLC on Windows XP.  

The jerkiness is very subtle when the videos are played at their actual resolution and most noticeable in fullscreen.  When their is a lot of action going on in the video it appears that the fields in the interlaced scan pattern are lagging and overlapping (but I don't even think they are interlaced videos).

I don't know if this is a driver issue or what, but I remember my friend had the same problem to a much lesser extent playing videos with VLC on his iMac.

If anybody thinks they could help me fix this I'd really appreciate it, I hate to have to reboot into Windows when I want to watch a movie.  Thanks.

---

### Post by trippinnik on 2007-06-12
I've had this problem too (may be related to a relatively slow CPU) but have had goodluck using totem-xine.  You can grab it in the repositories.

---

### Post by clk99 on 2007-06-13
Definitely not a hardware issue as the Windows installation that plays the videos fine is on the same system.  I'll give totem-xine a shot, thx.

---

### Post by clk99 on 2007-06-13
This may be a dumb question, but how do I run it? Do I have to remove totem-gstreamer first?

---

### Post by clk99 on 2007-06-17
bump

Still haven't figured this out, totem-xine didn't help. :/

---

### Post by clk99 on 2007-06-17
Fixed my problem by switching to fglrx display driver. :D

---

