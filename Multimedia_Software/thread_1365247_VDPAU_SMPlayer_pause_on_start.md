---
title: "VDPAU SMPlayer pause on start"
date: 2009-12-27
forum: Multimedia Software
---

### Post by Tyr_7BE on 2009-12-27
Hello

I'm trying to get SMPlayer working with VDPAU.  It's pretty much there - once you get a H264 mkv file playing, it plays super smooth and luxuriously.  However, my problem is with starting the file.  As soon as I open the file and press play, the time slider at the bottom stays at zero and I'm stuck looking at the first frame of the video.  If I press "jump forward 10 seconds", that seems to wake it up, and the video starts playing from 10 seconds in.  Same thing if I move the slider - the video will start playing from wherever the slider was dropped.  But I am unable to just press play and have the video start - I have to jump through these hoops.

Anyone have any ideas?  Google has so far turned up nothing.

---

### Post by lidex on 2009-12-27
Are you using these packages:
[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/~nvidia-vdpau/+archive/ppa")

---

### Post by rvm4000 on 2009-12-27
If you're using alsa as audio output, change it to pulse or oss (preferences -> general -> audio).

---

### Post by Tyr_7BE on 2009-12-27
Changing the sound target fixed it.  Thanks a lot!  I hoped someone would reply, didn't think it would be the SMPlayer developer :)

Much obliged, and thanks for your work on such an awesome program.

---

