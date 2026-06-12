---
title: "Webcam Issue: Logitech Quick Cam Fusion"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by rahulthewall3000 on 2007-05-01
Hi all!

I am asking this all over again, and I have yet not found any suggestions that could help me. I have a logitech quick cam fusion webcam and I have installed the drivers for the webcam using the information here:

[http://ubuntuforums.org/showthread.php?t=194793](http://ubuntuforums.org/showthread.php?t=194793)

Well, the drivers compiled without any issue. The Problem is that there is no software available that I can use to record video from my webcam. Only Ekiga recognizes my webcam as a video input source and I can not use that to record video.

So, if there is any software that anyone is aware of, kindly tell me.

Cheers
Rahul

---

### Post by phollands on 2007-05-04
Rahul

I managed to video showing locally in the following way ...

sudo chmod /dev/video 666
sudo ln -s /dev/video0  /dev/video

Then I run up Ekiga.
Under Edit / Preferences look for "Video Devices"
Choose the Video Plugin V4L2 then press Detect Devices
You should then get an input device option of 
USB Video Class Device.

I close that window and then setup view local video and I was in business with the
webcam showing on my local screen.

All this under Feisty without any other changes but fully up to date.

Peter

---

