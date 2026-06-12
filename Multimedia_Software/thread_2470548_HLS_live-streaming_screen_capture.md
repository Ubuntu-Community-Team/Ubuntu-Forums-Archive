---
title: "HLS live-streaming screen capture?"
date: 2022-01-03
forum: Multimedia Software
---

### Post by wangosteen on 2022-01-03
Would there be any way to livestream my screen capture (video and audio) on localhost in an HLS format? Would I have to use NGINX or is there an alternative? How would encoding work with a live stream?

---

### Post by TheFu on 2022-01-03
There are hardware live-streaming devices that sit between the computer and the monitor which handle the encoding/transcoding and streaming. Think those devices run ~ US$250 and don't need any specific OS to work.

[https://smile.amazon.com/Capture-Recorder-Device-Streaming-Windows/dp/B08R9PVJ3V](https://smile.amazon.com/Capture-Recorder-Device-Streaming-Windows/dp/B08R9PVJ3V)  is an example of a no-name version.

[https://smile.amazon.com/Elgato-Cam-Link-Broadcast-Camcorder/dp/B07K3FN5MR](https://smile.amazon.com/Elgato-Cam-Link-Broadcast-Camcorder/dp/B07K3FN5MR) <--- name brand version. From a review:
>  Despite the title, this can't do 4K on Linux, even at 30 FPS.
The highest resolution it supports at all is 1080p, per ffmpeg:
[video4linux2,v4l2 @ 0x56056c022100] Raw : yuyv422 : YUYV 4:2:2 : 1920x1080
[video4linux2,v4l2 @ 0x56056c022100] Raw : nv12 : Y/CbCr 4:2:0 : 1920x1080
[video4linux2,v4l2 @ 0x56056c022100] Raw : yuv420p : Planar YUV 4:2:0 : 1920x1080 

I don't livestream myself, so no clue about that.

I do have an HDMI capture device that sits between the output HDMI and the input monitor. It captures directly to storage (only NTFS/FAT32 supported). The saved video is h.264 encoded video + AAC stereo audio in 2GB MP4 containers.  In sequentially named files.  It only supports 1080p @ 30fps, but it was less than half the cost of other options.  HLS doesn't matter at all.

Do you intend to have people hit a server you run?  If not, then the video streaming site will handle the HLS quality and all the bandwidth issues.  You just need sufficient upstream bandwidth to push the quality video + audio required.  20Mbps up should easily cover all 1080p resolutions.  Perhaps 40Mbps for uncompressed 4K video. Better to have more than not enough.  If you have 20 people watching, I wouldn't let them connect to my server at home and I certainly don't want the headaches for solid bandwidth or security issues involved.  Let Twix or livestream or youtube handle those things.

---

