---
title: "Mplayer Fatal Error - no video"
date: 2009-11-13
forum: Multimedia Software
---

### Post by Drejcek on 2009-11-13
Hi!

I have installed Ubuntu 9.10 and Mplayer. When I try to open .avi file a get this Fatal Error:
[img]http://www.shrani.si/f/3o/TS/3lHmTHAb/screenshot-fatal-error.png[/img]

I also installed all GStreamer codecs.

---

### Post by andrew.46 on 2009-11-13
Hi Drejcek,

> **Drejcek said:**
> I have installed Ubuntu 9.10 and Mplayer. When I try to open .avi file a get this Fatal Error:
[img]http://www.shrani.si/f/3o/TS/3lHmTHAb/screenshot-fatal-error.png[/img]

I assume this is the GMPlayer front-end gui for MPlayer which I will admit I have not used for a while. But the solution is simple enough, just have a look through the video preferences and select another *video out* device. Usually x11 is a safe option. BTW you might find that SMPlayer gives a nicer interface and is available from the Ubuntu repositories.

All the best,

Andrew

---

