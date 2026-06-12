---
title: "mplayer error - Cannot dump this stream"
date: 2010-11-26
forum: Multimedia Software
---

### Post by c_calvin on 2010-11-26
I am trying to record down a video stream from an IP camera.

i can view the stream with

```
mplayer rtsp://192.168.2.6/play1.sdp
```However when i tried to save the stream by using 

```
mplayer -dumpstream rtsp://192.168.2.6/play1.sdp -dumpfile /home/test.avi

```I got the following error
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://192.168.2.6/play1.sdp.
Resolving 192.168.2.6 for AF_INET6...
Couldn't resolve name for AF_INET6: 192.168.2.6
Connecting to server 192.168.2.6[192.168.2.6]: 554...
A single media stream only is supported atm.
rtsp_session: unsupported RTSP server. Server type is 'unknown'.
STREAM_LIVE555, URL: rtsp://192.168.2.6/play1.sdp
Cannot dump this stream - no file descriptor available.

```How can I solve the file descriptor problem? Anyone can help? 
Thanks a lot ;)

---

