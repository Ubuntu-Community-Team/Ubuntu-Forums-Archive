---
title: "[SOLVED] Webcam"
date: 2008-12-24
forum: Multimedia Software
---

### Post by thunderbirdje on 2008-12-24
Struggling...

Webcam works with **cheese** not with **VLC**.

In VLC I used: File > Open Capture Device: changed *Video Device Name* into */dev/video0*. I see the time incrementing but no video. Even when I record to a file. No Video in the output file. 

What I see is that cheese is using v4l2, while VLC uses v4l (shows up in the status bar). I also noticed that in cheese the blue LED (indicator webcam is on) is on while it doesn't turn on in VLC.

Output of **cheese -v**
> andy@feng:~$ cheese -v
Detected webcam: HP Webcam
device: /dev/video0
video/x-raw-yuv 160 x 120 num_framerates 6
24/1 20/1 15/1 10/1 5/1 1/1 
video/x-raw-yuv 176 x 144 num_framerates 6
24/1 20/1 15/1 10/1 5/1 1/1 
video/x-raw-yuv 320 x 240 num_framerates 6
24/1 20/1 15/1 10/1 5/1 1/1 
video/x-raw-yuv 352 x 288 num_framerates 6
24/1 20/1 15/1 10/1 5/1 1/1 
video/x-raw-yuv 640 x 480 num_framerates 6
24/1 20/1 15/1 10/1 5/1 1/1 
v4l2src name=video_source device=/dev/video0 ! video/x-raw-yuv,width=640,height=480,framerate=24/1 ! identity


HELP :-) I would love to be able to control the output video format etc in VLC...

---

### Post by thunderbirdje on 2008-12-25
I installed the newest version of VLC [(instructions here)]("http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/") (0.9.8a Ghrisenko) which works with V4L2. 

Works fine now!

Maybe because the newer version of VLC is using V4L2? Maybe V4L in the older version doesn't support my HB Webcam.

---

