---
title: "Converting HD WMV to MKV"
date: 2011-03-20
forum: Multimedia Software
---

### Post by damnated on 2011-03-20
I have quite a few HD WMV files on my hard drive and it's a pain in the *** to play these on Ubuntu, since it eats up a lot of CPU. I use vdpau with SMplayer, so MKV's work well, that is why I would like to convert these WMVs to MKV, without losing quality. 
Is this possible with software for ubuntu?

---

### Post by vanadium on 2011-03-20
If you want to do this without loosing quality, you won't obtain video that is easier on your system. wmv is a container format, and so is mkv. The hard work, though, is in decoding the video stream. So if you do not change that, the video will remain choppy, whether it is in an mkv container or not.

If it is a full HD video, you should probably rescale it to 720p video, which is still very enjoyable in quality, and typically will still play well on a wider range of systems.

Handbrake can be used to convert video's, but I am not sure it supports wmv. Somewhat more difficult to use but much more powerful is avidemux. You could also try if winff could do a conversion that suits you, or you may define your custom profile.

---

### Post by damnated on 2011-03-20
Thanks for the quick response.

---

