---
title: "Poor performance in youtube fullscreen videos"
date: 2010-12-21
forum: Multimedia Software
---

### Post by Eppendecker on 2010-12-21
Hello,

I'm new to Ubuntu and Linux in general. I recently installed Ubuntu 10.10 on my old laptop and I'm very happy with the result. There's only one issue: the video performance in youtube full screen videos is very poor. The image is jerky with only about 5 fps. Sound is OK. In "normal" (not full screen) mode the videos work perfectly. I tried watching videos in different qualities (240, 320 etc.) but the result is always the same. Is this a software problem or is my laptop hardware just too underpowered? My specifications:

Fujitsu Siemens Amilo A7645
AMD Turion 64 mobile technology MT-28 / 1.6 GHz
SIS M760 integrated video card
Browser: Google Chrome, latest stable version

---

### Post by gordintoronto on 2010-12-21
The combination of a slow CPU and a very weak video adapter is the problem.

---

### Post by Eppendecker on 2010-12-22
Thanks. I am a little surprised because I also tried to play a DVD (using the movie player that came with the standard Ubuntu installation) and the performance was also unacceptable. I used to have Windows XP in this same laptop and was able to watch DVDs with good image quality. Why was the performance better on Win XP than Ubuntu 10.10?

---

### Post by gordintoronto on 2010-12-22
I don't know. There might be a specific video driver for your video adapter for XP, and perhaps it is OK.

---

### Post by picklemonkey on 2010-12-27
I was also experiencing this problem on a brand new custom-built computer with 4GB RAM and a 1GHz, 64-bit Graphics card.  I just did some searching on the forums and found this solution that just fixed my issue.

> **Ringi said:**
> Try, right click on the video window > settings > uncheck &#8220;Enable Hardware Acceleration&#8221;


It was checked; I unchecked it then pressed play on the video and speed went to where it should be.  I hope it helps!

---

