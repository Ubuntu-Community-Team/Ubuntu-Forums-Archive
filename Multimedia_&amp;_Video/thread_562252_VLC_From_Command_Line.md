---
title: "VLC From Command Line"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by anton_pm on 2007-09-28
Hi Guys,

I'm trying to run VLC on the command line from another machine and am getting this:

anton@anton-main:~$ vlc arrested.development.301.hdtv-lol.[VTV].avi :sout=#transcode{vcodec=h264,vb=1024,scale=1,acodec=mp4a,ab=192,channels=2}:duplicate{dst=std{access=file,mux=ts,dst="/home/anton/Desktop/test.mp4"}}
VLC media player 0.8.6 Janus
starting VLC root wrapper... using UID 1000 (anton)
Error: Unable to initialize gtk, is DISPLAY set properly?

Is there a way to get around this?

---

