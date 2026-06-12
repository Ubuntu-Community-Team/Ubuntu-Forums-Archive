---
title: "Recording audio using vlc"
date: 2010-02-03
forum: Multimedia Software
---

### Post by sam123 on 2010-02-03
I've been able to play both audio and video using vlc with:

vlc v4l2:// :input-slave=alsa://plughw:U0x46d0x9a2

(it accesses the default video device which is /dev/video0)

Is there any way in which I can have vlc access only the microphone and not the video device?

Solution:

vlc alsa://plughw:U0x46d0x9a2

---

