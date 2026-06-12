---
title: "Video jitter - Hulu - Intel Atom ion board"
date: 2010-07-18
forum: Multimedia Software
---

### Post by buddiemac on 2010-07-18
I have a ASROCK A330ION board with a Nvidia GeForce graphic chip.

- Graphic driver revision (195.36.24) and 2Gig of DDR3 Memory. 
- When streaming Hulu I use the application Hulu desktop. 
- My network connection is a wired ethernet connection. 
-The monitor resolution is 1080i 60hz.
-OS Lucid 64bit

All works quite well, but have problem with streaming video. When I stream video from Hulu there is a lot of jitter. If I lower the video quality settings in Hulu to low, then the video is acceptable.

I am not sure why this is. I have read that this board should easily handle streaming video. I believe the video line rate for high quality Hulu is 480.

Any others have experience with Atom and vieo jitter when streaming

---

### Post by buddiemac on 2010-07-19
I believe I have gotten the answer to this problem. Hulu uses the Flash player which is not able to take advantage of the Nvidia Drivers. Since the Atom is a relatively low performance it requires the NVIDIA IC for Graphic acceleration.

The Same problem is with Mplayer since it is not typically compiled for VDPAU. VDPAU allows for your graphic card/chip vs your CPU to process graphic information

Using XBMC is great for Videos but Hulu is not supported. I think this thread is solved.

---

