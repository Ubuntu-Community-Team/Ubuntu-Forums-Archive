---
title: "Problems playing mp4 videos in karmic"
date: 2009-11-26
forum: Multimedia Software
---

### Post by lullabong on 2009-11-26
Hello,

I am having problems to play video imported from a Sanyo VPC-HD2000 camara. I am running Karmic Koala on a Dell inspiron 1525. It imports it in mp4 format... and the problem is when I play the video (I've tried so far MPlayer, VLC, movie player, real player and so on...) it jumps at the highest resolution 1080 at 60 FPS and 30 FPS, but i think it is fine at 720 at 30 FPS. Although the video is jumping at 1080, the audio plays fine all the way through, with no jumps. 

Any ideas towards what I am doing wrong here?

Any help will be greatly appreciated.

Lulú

---

### Post by X-Rated on 2009-11-26
Hi, I have a similar camera. I don't know the specs for your Dell, but for 1080p60, 1080i60 and 1080p30 you will need avchd video acceleration (nvidia vdpau) or mplayer-mt (for dual core).

hth.

---

### Post by lullabong on 2009-11-30
Hi,

Thanks... it seems its my computer then...

:(

---

