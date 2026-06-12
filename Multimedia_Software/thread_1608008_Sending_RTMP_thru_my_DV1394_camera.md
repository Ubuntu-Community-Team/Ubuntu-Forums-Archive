---
title: "Sending RTMP thru my DV1394 camera"
date: 2010-10-28
forum: Multimedia Software
---

### Post by natanael68 on 2010-10-28
I'm using Maverick AMD64, and I'm trying to use ffmpeg latest to send video from my DV camera. Because ffmpeg may acquire video using v4l drivers, I decided to use dv4l to do it.
I dowloaded dv4l, installed the loopback module (also dv1394 and raw1394).
I ran dv4l and it says that I can use /dev/video1 for my camera.

So I just entered the ffmpeg command:
ffmpeg -r 25 -s 352x288 -f video4linux -i /dev/video1 -re -acodec libfaac -ar 22050 -vcodec libx264 -vpre basefile -f flv rtmp://flashserver/app/stream

But this is the message I get:

[video4linux @ 0xd5b4f0] Fatal: grab device does not handle capture
/dev/video1: Input/output error

Any of you have succeded to capture from a DV1394 camera using V4L ?
Can you help me please ?
thanks and regards

---

