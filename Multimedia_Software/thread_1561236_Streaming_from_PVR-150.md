---
title: "Streaming from PVR-150"
date: 2010-08-26
forum: Multimedia Software
---

### Post by dedno on 2010-08-26
I have installed successfully a PVR-150 TV tuner.  I can change the channel and use cat to make a recording.  What I would like to do is stream the video and audio from the current channel to another computer on my LAN.  I don't want anything nearly as complex as MythTV, and have been looking into using VLC.  Unfortunately, I cannot get it to work.

I use the following command to launch the VLC stream.
```
vlc -vvv v4l2:///dev/video1:input=2:audio-input=1:standard=8:volume=54272 --sout '#transcode{vcodec=mp4v,acodec=mpga,vb=800,ab=128}:standard{access=http,mux=ogg,dst=192.168.0.100:8080}'
```
The command appears to be successful, but I cannot connect to the stream from another computer using VLC.  On the client, I enter [http://192.168.0.100:8080](http://192.168.0.100:8080) as the network URL, but VLC cannot seem to connect.

What am I doing wrong?

---

