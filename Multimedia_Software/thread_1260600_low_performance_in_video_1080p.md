---
title: "low performance in video 1080p"
date: 2009-09-07
forum: Multimedia Software
---

### Post by webkage on 2009-09-07
I am trying to play some .mkv 1080p videos on Ubuntu 9.04, I tried VLC, smplayer, etc... but still have some problem with the performance, some framedropping and so.

The point is in Windows work perfect with the VLC. I guess is something going on with the nvidia configuration and in somewhere its activate some kind of postprocessing for quality, I have a GeForce 9800GT using last drivers 180 and a Q6600 processor with 2 Gb RAM, so the machine is not the problem.

My question is, where and what I must start looking for? I dont know if the nvidia-setting has something to do with the video output, or if I must change something in the xorg. I am a little bit lost.

---

### Post by denver on 2009-09-07
Nvidia cards starting with 8 series can take advantage of VDPAU (Video Decode and Presentation API for Unix). Here is a thread that details VDPAU a bit and shows how to get it working:

[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

You should see a significant performance boost and minimum CPU usage while usgin VDPAU.

Good luck!

---

### Post by xenogia on 2009-09-07
You can add the latest Mplayer and SMPlayer repository and get those apps and you can take advantage VDPAU out of the box.  Definetly recommended :)

[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")
[https://launchpad.net/~rvm/+archive/smplayer]("https://launchpad.net/%7Ervm/+archive/smplayer")

Smplayer acts as a frontend for MPlayer and in the preferences menu just choose VDPAU as your output.

This will work as long as your Nvidia card supports it.

---

