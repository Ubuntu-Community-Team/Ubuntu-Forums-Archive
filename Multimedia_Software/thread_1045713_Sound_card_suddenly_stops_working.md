---
title: "Sound card suddenly stops working"
date: 2009-01-20
forum: Multimedia Software
---

### Post by neoncode on 2009-01-20
I have two sound cards in my PC. A Sound Blaster Audagy 2 ZS that I use though an amp + speakers for music/videos and such. Along with a motherboard-interated nvidia sound card connected to a couple of tinny speakers for system notifications and the like.

Now, I use KDE4 so I use it's sound config to make KDE4 send all it's notifications direct to the nvidia card's device. All other sound it sends though pulse audio. All other programs (firefox, Amarok) just play though pulse audio too. 

Now pulse detects both sound cards but has the Sound Blaster's sink set as its default. This all worked perfectly up untill about an hour ago after a kernel update. After I restarted, the nvidia integrated thing works as usual but the sound blaster gives no sound at all.

I have tested the amp + speakers and the cable connecting them with other devices. I have made sure nothing is muted and all audio sliders are set to maximum. Even pulse audio's little monitor thing showing the volume levels being sent to the sinks shows output. But I hear nothing.

Even when I try "cat /dev/urandom > /dev/dsp" (The sound blaster's device) I hear nothing.

Can anyone give any advice?

---

