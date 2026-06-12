---
title: "[SOLVED] Please Help my Laptop Freezes Everytime I Use Video"
date: 2008-11-11
forum: Multimedia Software
---

### Post by volaer on 2008-11-11
Hi, I am really having a hardtime, figuring out how to solve this problem.

Here's the specs of my laptop:

Laptop Model: Acer Aspire 4330-592G32Mn
([http://www.acer.com.ph/notebook.php?pkey=123](http://www.acer.com.ph/notebook.php?pkey=123))

Processor Type: Intel Celeron M 575 (2.0GHz, 1MB, 667FSB)
Chipset: Mobile Intel® GL40 Express Chipset
Memory: 1GB DDR2 RAM
Video Type: Intel® Graphics Media Accelerator 4500M with up to 1759 MB of Intel DVMT 5.0 (64 MB of Dedicated Memory, up to 1695 MB of Shared Memory )
	
56K Modem and Gigabit LAN
Wireless LAN Built in Wireless LAN (802.11a/b/g/Draft-N) Wireless (Atheros AR5B91 Wireless Network Adapter)

Card Reader:   Built in 5 in 1 Card Reader
Built-in Camera: Acer CrystalEye Webcam

Whenever I play video files in my Totem, or even play mp3 or music that will use visualization, my entire laptop freezes, all the sofwares, windows, etc, except my cursor.

I cannot reset it because this model of laptop does not have any reset button. 
Please, tell me what's wrong with my laptop... Was it my video driver? Honestly I really don't know how to update my video driver with the right one. Help please.... 

If my multimedia, video, and audio will work with no problem + my wireless Atheros AR5B91, I will totally shift to ubuntu and will not use windows XP anymore. 

I really love ubuntu, but this problem with my notebook is giving me a headache. 

Anyone please???

---

### Post by Hyssar on 2008-11-15
It is sure not the best advice you could get, but Im doing my best to help you. Just install the package vlc with synaptic and try playing your files with it. If it doesn't help... I would try to find some drivers for that graphic card.

Hope it helps,

Hyssar

---

### Post by killer_d76 on 2008-11-16
try to disable "PulseAudio" perhaps that should fix the issue! ;)

---

### Post by volaer on 2008-11-17
How can I disable Pulse Audio? and how does it connect to the freezing of my video files? My audio is doing fine and I don't have any problem with it except when when i play video files, then everything freezes.

---

### Post by psyke83 on 2008-11-17
PulseAudio is not causing the freezes, don't listen to any advice to disable it.

If you are using Intrepid, I recommend you wait for an [update]("https://lists.ubuntu.com/archives/intrepid-changes/2008-November/009492.html") to the Intel driver that should be built and uploaded some time today - it may fix your problem.

In the meantime, open a terminal and launch "gstreamer-properties". Click the Video tab, and for "Default Output", choose "X Window System (No Xv)".

Please let me know if you can play video in Totem without freezes.

N.B. That setting will disable Xv output, meaning that the video will be 100% software rendered. This is slower and lower quality. Be sure to set the option back to "Autodetect" after the driver update is installed.

---

### Post by volaer on 2008-11-17
> **psyke83 said:**
> PulseAudio is not causing the freezes, don't listen to any advice to disable it.

If you are using Intrepid, I recommend you wait for an [update]("https://lists.ubuntu.com/archives/intrepid-changes/2008-November/009492.html") to the Intel driver that should be built and uploaded some time today - it may fix your problem.

In the meantime, open a terminal and launch "gstreamer-properties". Click the Video tab, and for "Default Output", choose "X Window System (No Xv)".

Please let me know if you can play video in Totem without freezes.

N.B. That setting will disable Xv output, meaning that the video will be 100% software rendered. This is slower and lower quality. Be sure to set the option back to "Autodetect" after the driver update is installed.


It worked!!! many thanks!!!

---

