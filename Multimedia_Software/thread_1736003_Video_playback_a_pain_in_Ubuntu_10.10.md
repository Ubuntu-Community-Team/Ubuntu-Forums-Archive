---
title: "Video playback a pain in Ubuntu 10.10"
date: 2011-04-22
forum: Multimedia Software
---

### Post by tropical22 on 2011-04-22
OMG! I re-installed Ubuntu 10.10 a couple of times and still video playback seems to be a major problem: it is choppy and stuttery at best, both the pictures and the sound. The longer I play a video, the lower the quality gets; I've installed all those gstreamer drivers and the usual stuff, never really had a problem with video playback with Ubuntu 9.10 and pevious versions. :(

No matter which player I use, the quality problem persists..... Please could you help me with this, my laptop is a Lenovo G550 and has thus far been a great machine for Linux users! Thanks a bunch for your assistance in advance!!!
:)
tropical22

---

### Post by owise1 on 2011-04-22
is this for flash video or all videos

---

### Post by K_45 on 2011-04-22
Open a terminal and

```
vlc filename
```

where filename is the name of the video file, remember to add in the extension. Then post the output of terminal after you skip through the video. Are these 1080p files?

---

### Post by beew on 2011-04-22
That depends on hardware as well. I play 1080p in 10.10 flawlessly on my laptop (Nvidia G105, dual core) with both the proprietary driver and nouveau (I have another 10.10 installed on an external drive which uses only the open source drivers so it can boot from any machine) The only difference is there is some tearing in nouveau and it uses 40-60% cpu instead of 10-20% with VDPAu. On older machines with weaker cpu there is a problem because the cpu can't handle the decoding.

You need to tell people the specs of the computer.

---

### Post by doas777 on 2011-04-22
you said performance seems to degrade with use?
what is your CPU temperature?
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by KegHead on 2011-04-22
Hi!

Just curious about your temp.

If you're running hot, it could be a kernel upgrade need.

Your kernel manages several parameters..temp, disks etc.

Have you;

sudo apt-get update

sudo aptitude install linux-image -f

Recently.

KegHead

---

### Post by Guzpido Krush on 2011-04-22
i tried to fix this issue by forcing GStreamer to use VDPAU (PureVideo) NVIDIA technology on my videocard:

[http://ubuntuforums.org/showthread.php?t=1736584](http://ubuntuforums.org/showthread.php?t=1736584)

gnome-mplayer might be another, fastest way, to accomplish that, since ffmpeg has VDPAU technology implemented in it (by NVIDIA folks)

# apt-get install gnome-mplayer

---

### Post by doas777 on 2011-04-22
MPlayer is a smoother backend, so I usually use SMPlayer from the PPAs
[https://help.ubuntu.com/community/SMPlayer](https://help.ubuntu.com/community/SMPlayer)
better interface than gmplayer, but the same great backend. 
op, we assume you have installed the mediubuntu w32/64 codec bundle and the ubuntu-restricted-extras package as well.

---

### Post by beew on 2011-04-22
> **doas777 said:**
> MPlayer is a smoother backend, so I usually use SMPlayer from the PPAs
[https://help.ubuntu.com/community/SMPlayer](https://help.ubuntu.com/community/SMPlayer)
better interface than gmplayer, but the same great backend. 
op, we assume you have installed the mediubuntu w32/64 codec bundle and the ubuntu-restricted-extras package as well.


I just found an even better front end to mplayer than Smplayer. Check out the Umplayer (which is a fork for Smplayer)

[http://www.umplayer.com/](http://www.umplayer.com/)

---

### Post by doas777 on 2011-04-22
> **beew said:**
> I just found an even better front end to mplayer than Smplayer. Check out the Umplayer (which is a fork for Smplayer)

[http://www.umplayer.com/](http://www.umplayer.com/)
Kewl! I'll have to check it. Thx!

---

