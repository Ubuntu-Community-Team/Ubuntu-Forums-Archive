---
title: "mplayer-vdpau package."
date: 2009-05-01
forum: Multimedia Software
---

### Post by odror on 2009-05-01
Is there a repository having compiled version of mplayer-vdpau
for ubuntu 9.04 from a repository (actually mythbuntu 9.04).

I prefer to download a package rather than compile it. I want to keep my system integrity for future upgrades.

thanks

---

### Post by inobe on 2009-05-01
simply get ffmpeg and mplayer

then run this in terminal to check

```
ffmpeg -formats | grep vdpau
```


you should see something similar to this

```
D V D h264_vdpau H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
D V D vc1_vdpau SMPTE VC-1 VDPAU
```

---

### Post by odror on 2009-05-01
Thanks

Is it my imagination? the HD image quality seems less than it is without VDPAU.


-Oz

---

### Post by KhaaL on 2009-07-22
inobe, do you mean that there is not required to do any configuration besides that in order to get vdpau running on jaunty?

> **inobe said:**
> simply get ffmpeg and mplayer

then run this in terminal to check

```
ffmpeg -formats | grep vdpau
```


you should see something similar to this

```
D V D h264_vdpau H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
D V D vc1_vdpau SMPTE VC-1 VDPAU
```

---

