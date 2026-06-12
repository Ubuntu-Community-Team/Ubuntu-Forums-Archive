---
title: "Avidemux - No h264"
date: 2012-01-16
forum: Multimedia Software
---

### Post by Ph1b on 2012-01-16
Hey

I want to encode a vob file by using h264 with avidemux. But I cannot find it. How can I add h264 to Avidemux?

---

### Post by cotcot on 2012-01-16
It looks like you need to recompile avidemux to include h264. See [[COLOR="Red"]here[/COLOR]]("http://avidemux.org/admWiki/doku.php?id=tutorial:h.264").

---

### Post by bcarlowise on 2012-01-16
Try installing the libavformat-extra-53 package. I had to install that to get x264 support for Openshot and it might be what is missing on your system. I can convert videos using h.264 in AviDemux just fine.

---

### Post by cotcot on 2012-01-17
I checked the previous post. Indeed avidemux from the repository (so not recompiled) can open a h264 coded video. I only get an warning about maybe errors with B-frames and accuracy loss in frame number when a safer mode is accepted. I do not see the h264 codec in the list to use for conversion. I did a test and it worked fine.

---

### Post by alphacrucis2 on 2012-01-17
> **cotcot said:**
> I checked the previous post. Indeed avidemux from the repository (so not recompiled) can open a h264 coded video. I only get an warning about maybe errors with B-frames and accuracy loss in frame number when a safer mode is accepted. I do not see the h264 codec in the list to use for conversion. I did a test and it worked fine.

H.264 = AVC in the Avidemux output codec list.

See [this]("http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC").

---

