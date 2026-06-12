---
title: "cannot stream from command line"
date: 2010-02-22
forum: Multimedia Software
---

### Post by bandito40 on 2010-02-22
Hi,


I have gotten vlc to stream from a webcam using the gui however I cannot get the same from the command line. I would like vlc to start streaming as soon as Linux is done booting. The only way I can think of doing this is with the command line. The command that vlc gives when I get it to stream with the gui is:
**vlc v4l2:// :v4l2-dev=/dev/video0 :v4l2-adev= :v4l2-standard=0:sout=#transcode{vcodec=mp4v,vb=800,scale=1}:duplicate{dst=display,dst=std{access=http,mux=asf,dst=localhost:8080}} :sout-all :sout-keep**

This line opens vlc and a window for the video but does not stream.

Anyone know what I am doing wrong?

Thanks,

---

