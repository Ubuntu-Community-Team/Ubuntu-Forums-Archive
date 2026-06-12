---
title: "IEC958 Digital Out Stops After Glitch in Video Played in Xine"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by kidcharles on 2007-10-20
Hi all, I have a strange thing that has been happening occasionally. When watching a recorded HDTV video on Xine, which I have set up to do AC3 passthrough, sometimes when there is a glitch in the video the digital output shuts off. After that no sound will be output at all from any source. Running alsamixer shows that the IEC958 digital out is missing altogether. Doing '/etc/init.d/alsa-utils restart' brings back the digital out as a channel in alsamixer, but no sound is output. Restarting the computer fixes the problem. Is this just some massive bug? Any ideas on how to at least be able to get sound back without having to restart the computer? Thanks.

---

