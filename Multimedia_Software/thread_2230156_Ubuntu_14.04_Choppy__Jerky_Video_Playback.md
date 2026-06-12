---
title: "Ubuntu 14.04 Choppy / Jerky Video Playback"
date: 2014-06-17
forum: Multimedia Software
---

### Post by ap0ll0uk2 on 2014-06-17
I'm not quite sure what I've done wrong but I've noticed in the last couple of weeks that some of my avi files in XBMC have been suffering from choppy or and jerky playback. My TV playback is fine on my DVB-S tuner, and streaming video such as YouTube is also fine. The files are standard avi, not 1080p and watching them over the network on my Windows laptop is fine.

This evening I've tried an avi in Totem and it shows the same symptoms which leads me to believe that it's not really an XBMC issue but something underneath.

I'm running Ubuntu 14.04 x64, C2D 2.4GHz, 6GB Ram, 128GB SSD, nVidia GT 640 4GB, all connected to a 40" Samsung LCD TV via HDMI. I'm running the latest Ubuntu updates and I've tried nVidia proprietary drivers 304.117, 331.38 and the Nouveau drivers. The nVidia and Nouveau drivers both produce the same result. 

I'm not sure if a recent update has caused this issue or if its something else. Does anyone have any ideas please?

---

### Post by ap0ll0uk2 on 2014-06-21
-:[Bump]:-

---

### Post by sudodus on 2014-06-21
Maybe some daily update/upgrade caused the problem. ***Try booting with an older kernel*** (if you still have one).

Maybe it is the kind of file (the codec) that is more difficult to decode, or not possible for advanced decoding with the help of the graphics chip. ***Try some other avi*** file, that you know played well before.

While testing, run the ***system monitor*** or ***top*** or ***htop*** and watch the CPU usage. If it is close to 100%, the video playing will start lagging or skipping frames.

You might also ***check the settings in the video player***, and try to make it more light-weight (balancing quality and speed).

---

