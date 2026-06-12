---
title: "[gstreamer] Streaming video and audio of Logitech C920 Webcam"
date: 2014-05-08
forum: Multimedia Software
---

### Post by skipx on 2014-05-08
Not sure if this is the right place to ask but I found it difficult to find another forum about gstreamer!
I have the Logitech C920 webcam and want to make the video+audio stream available to another PC (using e.g. tcpserverlink). I want to use the camera's H264 stream since its pretty nice and compact. 
I'm already able to captsure the video + audio to hard disk with the command below:

gst-launch-1.0 v4l2src device=/dev/video1 ! video/x-h264,width=1280,height=720,framerate=30/1 ! h264parse ! \
muxout. \
pulsesrc device="alsa_input.usb-046d_HD_Pro_Webcam_C920_F1894590-02-C920.analog-stereo" \
! queue ! audioconvert ! voaacenc bitrate=65536 ! \
muxout. \
matroskamux name=muxout streamable=true ! \
filesink location=output-movie.mp4 

(using gsttreamer 1.2.3 in Ubuntu 14.04)
But now I would like to also make it available online. Afaik tcpserverlink would be ideal since it streams the source as is (right?) and I can use the pc with webcam as 'server'. This is preferable because of port settings. 

At this point I'm quite stuck.. Anybody has tips/solutions to get me on the road again?
Thanks!

---

