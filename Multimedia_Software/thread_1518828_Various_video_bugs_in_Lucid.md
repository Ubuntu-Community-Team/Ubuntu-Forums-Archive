---
title: "Various video bugs in Lucid"
date: 2010-06-27
forum: Multimedia Software
---

### Post by damnated on 2010-06-27
I did a clean install of Lucid, and almost everything video related is a little sluggish. First of all, Compiz is really slow compared to how it was in Karmic. 
I don't even use window animations, just the Scale and a couple other effects, like desktop cube. Scale is really slow, and sometimes it doesn't work. I have to start compiz again to get it working. Desktop cube actually froze a couple of times half way through a rotation. Rotating the cube is much slower as well. 

Also, I've been having a lot of trouble with HD video playback. It's not just the 100% CPU load that's bugging me, but every 3-4 minutes the playback skips frames, and the image becomes all glitchy. 

Flash playback also uses a lot of CPU, I can't even watch youtube videos in fullscreen most of the time. And I'm always opting for the lowest quality possible btw.

I have a dual core AMD CPU and 8600GT nvidia graphics card, so it's not a hardware issue. Please advise.

---

### Post by cchhrriiss121212 on 2010-06-28
Firstly what driver are you running? (system>hardware drivers)

Flash slows up on my machine too, which is a dual core 2.9GHz AthlonII 245, it has always been crummy for me. Flash is poorly designed for linux so it won't make use of any hardware acceleration and will suck up cpu power, but this is not the case with HD videos in standalone players.

As you have an nvidia card, you can make use of vdpau video output in mplayer or xine. It should be working by default in lucid, install smplayer, then select vdpau under video output preferences. With vdpau you will only use 10% cpu even with 1080p video.

---

### Post by damnated on 2010-06-28
Lol, I never thought about updating the driver, I had the 173 version, updated now and it Compiz works a lot better now. 

The vdpau output doesn't work though. I set it as my output, and now there is no video, only the audio is playing. The player is minimized as well, as if the file was only an audio file.

---

### Post by cchhrriiss121212 on 2010-06-28
I think vdpau needs at least the 185 drivers to work, but I assume you went to the 195 series.
Which video player were you using? Try adding yourself to the video group, or switching to the other player

---

### Post by damnated on 2010-06-28
Actually I don't know what version is installed now, because in Hardware Drivers it only says NVIDIA accelerated graphics driver (version current), and that this is the recommended version.

I was playing the file in smplayer.

---

### Post by damnated on 2010-08-05
After installing vdpau with ```
libvdpau-dev
``` vdpau finally works, with a minimal CPU load this time :D

---

