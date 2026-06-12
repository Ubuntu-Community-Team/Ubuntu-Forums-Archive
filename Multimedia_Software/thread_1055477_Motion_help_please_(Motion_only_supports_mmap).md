---
title: "Motion help please (Motion only supports mmap) ??"
date: 2009-01-30
forum: Multimedia Software
---

### Post by RaeMarvin on 2009-01-30
Hi I'm trying to get Motion to work with my Webcam and hope someone can help.

I'm using Ububntu 8.10 with a webcam Logitech Quickcam Chat.

I have used EasyCam to install the driver and tested it with Cheese Webcam Booth. 

I then Installed Motion through Synaptic.

When I try to start Motion I get the below.

[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.9 Started
[0] ffmpeg LIBAVCODEC_BUILD 3355136 LIBAVFORMAT_BUILD 3409664
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[1] cap.driver: "ivtv"
[1] cap.card: "Hauppauge WinTV PVR-150"
[1] cap.bus_info: "0000:02:09.0"
[1] cap.capabilities=0x01070051
[1] - VIDEO_CAPTURE
[1] - VBI_CAPTURE
[1] - TUNER
[1] - AUDIO
[1] - READWRITE
[0] motion-httpd/3.2.9 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8080
[1] Supported palettes:
[1] 0: HM12 (HM12 (YUV 4:2:0))
[1] 1: MPEG (MPEG)
[1] Unable to find a compatible palette format.
[1] ioctl(VIDIOCGMBUF) - Error device does not support memory map
[1] V4L capturing using read is deprecated!
[1] Motion only supports mmap.
[1] Capture error calling vid_start
[1] Thread finishing...

Could someoen help me to sort this out with Motion if not is there another motion detector I could use.

Thanks in advance

Rae

---

### Post by RaeMarvin on 2009-01-31
Hi all,

I have managed to sort it out. Silly mistake I had set Motion to monitor the wrong device. Once I had changed that in my motion.conf file it works like a dream (well so far).

Cheers anyway
Rae

---

