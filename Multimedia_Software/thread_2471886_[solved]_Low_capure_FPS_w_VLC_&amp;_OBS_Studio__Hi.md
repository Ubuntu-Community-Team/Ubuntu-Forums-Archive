---
title: "[solved] Low capure FPS w/ VLC &amp; OBS Studio / High capture FPS w/ Google Meet &amp; Zoom"
date: 2022-02-11
forum: Multimedia Software
---

### Post by daddingtonpalace on 2022-02-11
**Problem: **I'm getting very low frame-rate (e.g. 5 FPS) capturing a USB capture device from VLC and from OBS Studio. But I get normal frame-rate (maybe 30 FPS) when I capture the same device from Google Meet or Zoom. Any idea where I can get help understanding the issue?

[B]Details:
[/B]Google Meet and VLC are both opening the same underlying device /dev/video0, presumably OBS too. After burrowing around a bit in the VLC interface I can see that framerate on the capture device is set to 60fps (which ain't happening obviously).

The capture device is a cheapo Amazon HDMI > USB capture card:
> BlueAVS HDMI to USB Video Capture Card 1080P

**Sysinfo:**
> OS: Ubuntu 21.10 x86_64 
> Kernel: 5.13.0-28-generic 
> CPU: AMD Ryzen 5 PRO 4650G with Radeon Graphics (12) @ 3.700GHz 
> GPU: AMD ATI 05:00.0 Renoir 
> Memory: 2892MiB / 27966MiB 
Any advice would be appreciated.

---

### Post by Autodave on 2022-02-11
My guess would be that the faster frame rates are because the program is using a smaller picture....less pixels.  Try using a lower resolution setting on your webcam.

---

### Post by daddingtonpalace on 2022-02-12
Okay. That wasn't *exactly* the answer, but it was close and it nudged me into the right answer. Reducing resolution did increase framerate. But the real fix for me was to select a different "Video Format" for the capture device. It was using "YUYV 4:2:2" which resulted in very low framerate. Switching to any of the other available formats did the trick.

Turns out 
- YUYV 4:2:2 > uncompressed video with high bandwidth requirements
- BGR3 (Emulated) > compressed video in mjpg format 
- YU12 (Emulated) > compressed video in mjpg format 
 - YV12 (Emulated) > compressed video in mjpg format 

Any of the compressed formats produced 60fps at 1920 x 1080. Nice!

Discovering this I search around and found a good source of info on the different formats: [https://jpetazzo.github.io/2020/06/27/streaming-part-4-linux/](https://jpetazzo.github.io/2020/06/27/streaming-part-4-linux/)

Thanks for the nudge.

---

### Post by Autodave on 2022-02-12
Glad we "helped" a little!  Please remember to mark this thread as "Closed" by going to top of thread, Thread Tools.

---

### Post by linux-sysop on 2022-02-12
Just my 2 cents, I use a few various capture programs, I like vokoscreen the best and OBS second best.  The vokoscreen seems to chew up less resources, high frame rate, and gives great compression.

---

