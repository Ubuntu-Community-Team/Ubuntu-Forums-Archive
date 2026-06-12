---
title: "Transcoding RTSP to HTTP for Motion using VLC"
date: 2015-09-07
forum: Multimedia Software
---

### Post by olesk on 2015-09-07
Currently the official version of Motion does not support RTSP. There are forks which do, but I've been unable to get them to work properly, so I have decided to transcode my RTSP stream (from a webcam that only does RTSP) to MJPEG and HTTP using VLC.

The VLC command I use is as follows:
```

cvlc -I http rtsp://10.0.1.151:554/HighResolutionVideo :sout='#transcode{vcodec=MJPG,vb=800,fps=5}:std{access=http{mime=multipart/x-mixed-repace},mux=mpjpeg,dst=0.0.0.0:8989/go.mjpg,delay=0}'

```
This works well. If I start another VLC instance, I can view the video, including from a remote Windows box using VLC for Windows, with no special settings.

On the same machine as I do the transcoding, I have Motion (controlled by Motioneye) installed. This setup works just fine when streaming from a different camera using HTTP, but when trying to open the transcoded stream, Motion gives up. 

```

[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Processing config file thread-shadowcam2.conf
[0] Unknown config option "locate_motion_style"
[0] Motion 3.2.12 Started
[0] ffmpeg LIBAVCODEC_BUILD 3547904 LIBAVFORMAT_BUILD 3544067
[0] Motion running in setup mode.
[0] Thread 1 is from thread-shadowcam2.conf
[0] Thread 1 is device: http://localhost:8989/go.mjpg input -1
[0] Webcam port 8083
[0] Waiting for threads to finish, pid: 20714
[0] motion-httpd/3.2.12 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 7999
[1] Thread 1 started
[1] Camera thread starting...
[1] Unrecognized content type
[1] Error reading first header - re-trying
[1] Removed netcam Keep-Alive flagdue to apparent closed HTTP connection.
[1] Error reading first header - re-trying
[1] Unrecognized content type
[1] Error reading first header - re-trying
[1] Unrecognized content type
[1] Error reading first header - re-trying
[1] Unrecognized content type
[1] Error reading first header - re-trying
[1] Failed to read first camera header - giving up for now
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] Started stream webcam server in port 8083
[1] Resizing pre_capture buffer to 3 items
[1] Raw changes:     0 - changes after 'EedDl':     0 - labels:   0 - noise level: 21
[1] Raw changes:     0 - changes after 'EedDl':     0 - labels:   0 - noise level: 21
[1] Raw changes:     0 - changes after 'EedDl':     0 - labels:   0 - noise level: 21
[1] Retrying until successful connection with camera
[1] Camera thread starting...
[1] Unrecognized content type
[1] Error reading first header - re-trying
[1] Removed netcam Keep-Alive flagdue to apparent closed HTTP connection.
[1] Error reading first header - re-trying
[1] Unrecognized content type
[1] Error reading first header - re-trying
[1] Unrecognized content type
[1] Error reading first header - re-trying
[1] Unrecognized content type
[1] Error reading first header - re-trying
[1] Failed to read first camera header - giving up for now

```

I am by no means well versed in the intricacies of transcoding and codecs/protocols, so perhaps someone who knows this better can suggest a solution. I am guessing that my transcoded stream is somehow not acceptable to motion, but I'm at loss as to what can be done to fix it.

---

