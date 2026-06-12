---
title: "Big Problem with Integrated Logitech Quickcam &amp; Microphone (Dell XPS m1210)"
date: 2009-07-27
forum: Multimedia Software
---

### Post by cenobyte321 on 2009-07-27
Hi Ubuntu Community,

Just an hour ago I managed to get my Logitech Quickcam (that comes integrated on my Dell XPS m1210 laptop) to record audio and capture video in some applications like Sound Recorder and Cheese, there were some problems with these and other applications but that is not my main concern right now.

I have VMware with Windows XP installed and I tried to "connect" the camera to the Virtual Machine, a warning appeared that the device would be disconnected from the host so I pressed ok. I tried installing the camera and mic drivers in the VM but it failed.

So I restarted my computer, opened up Cheese and to my surprise a message saying "No Camera Found!" popped up. I then opened up Sound Recorder and I couldn't record anything, the application also crashes whenever I hit the "RECORD" button.

In the volume control I remember there were two ALSA mixers one that is "HDA Intel" (I presume it is the integrated soundcard) and other that is called "HDA USB Device" (The Logitech Quickcam Mic), but now only the first one appears. Basically I believe the VM disconnected completely the Quickcam USB device and Ubuntu wouldn't recognize it even after rebooting. 

So in a summary I would like to know if there's any way to reconnect an Integrated USB device like the Logitech Quickcam from Dell.

I hope you can help me with my screw up.

Thanks a lot.

PS: I'm using Ubuntu 9.04

---

### Post by cenobyte321 on 2009-07-27
anyone knows if this has a solution?

---

