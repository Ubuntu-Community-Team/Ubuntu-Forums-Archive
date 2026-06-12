---
title: "Playing MP4s"
date: 2009-09-25
forum: Multimedia Software
---

### Post by jamesdcarroll on 2009-09-25
I can't get MP4s to play in Totem (Gstreamer version or xine) or in VLC. I've tried everything that I could find that other folks have tried to no avail.  At this point it wouldn't surprise me if I've just messed things with all the installing.

If I just double click on the video it starts, then dies immediately (both Totem and VLC). If I start Totem then try to open the file, it tries then dies.  VLC on the other hand, just displays a blue square.

Any suggestions/help would be appreciated.

Thanks,

---

### Post by credobyte on 2009-09-25
Have you installed w32codecs and non-free-codecs from Mediabuntu ?

---

### Post by EV500B on 2009-09-25
You can try playing the mp4 on smplayer

---

### Post by jamesdcarroll on 2009-09-25
I hadn't so I did. 

No luck.

---

### Post by andrew.46 on 2009-09-25
Hi james,

> **jamesdcarroll said:**
> If I just double click on the video it starts, then dies immediately (both Totem and VLC). If I start Totem then try to open the file, it tries then dies.  VLC on the other hand, just displays a blue square.

Usually this is a sign of trouble with the default video-out. I am not familiar with Totem but certainly vlc has a setting under Tools --> Preferences --> Video where the setting can be changed from 'Default' to something like 'x11 video output'. This will not solve the underlying problem but may get your videos going anyway :).

Andrew

---

### Post by jamesdcarroll on 2009-09-25
That fixed it. At least for VLC.

THANKS!

---

