---
title: "[gstreamer] Merge Audio and Video pipelines"
date: 2014-10-13
forum: Multimedia Software
---

### Post by philippe9 on 2014-10-13
Hi everyone.

I have two different pipelines, one for video and one for audio. They both work independently but i'd like to merge them as a single one. I believe this is possible but i have no idea how to do such a thing :(

Here are my two pipelines:

Sender
```
gst-launch v4l2src device=/dev/video0 ! 'video/x-raw-yuv,width=1280,height=720,framerate=10/1' ! ffmpegcolorspace ! vpuenc codec=6 ! rtph264pay ! udpsink host=192.168.20.26 port=5000 

gst-launch alsasrc device=hw:2 ! audioconvert ! audioresample  ! alawenc ! rtppcmapay ! udpsink host=192.168.20.26 port=5001
```

Receiver
```
gst-launch udpsrc port=5000 caps="application/x-rtp, media=(string)video, clock-rate=(int)90000, payload=(int)96, encoding-name=(string)H264" ! rtph264depay ! ffdec_h264 ! xvimagesink

gst-launch udpsrc port=5001 caps="application/x-rtp" ! rtppcmadepay ! alawdec ! alsasink
```

Moreover, anyone knows what would be the resulting sdp file so i can also open it in VLC if needed?

Any pointers would be of great help ;)

Thank you.

---

### Post by Rob Sayer on 2014-10-14
I have no idea why you want to do such a thing.  There are a gazillion pipelines going on in linux all the time.  And a video file actually contains 2 streams, video and audio.

---

### Post by philippe9 on 2014-10-14
oh. I tought i had to merge them so i can record them as a single file :/
And also for A/V sync, no?

---

