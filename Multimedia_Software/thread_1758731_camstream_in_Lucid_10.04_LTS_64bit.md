---
title: "camstream in Lucid 10.04 LTS 64bit"
date: 2011-05-15
forum: Multimedia Software
---

### Post by makeiteasy on 2011-05-15
camstream worked fine with Ubuntu 8.04 LTS 64bit 

Since I installed 10.04.2 LTS 64bit , camstream is freezing when it opens the webcam. I have to kill it to end the freezing.

No change in hardware. 

Any solution? (or other software I can use to upload snapshots from webcam to my server)

---

### Post by no2498 on 2011-05-15
you try webcam studio yet

---

### Post by makeiteasy on 2011-05-17
Thanks for the reply,

I installed "webcam" through "Ubuntu Software Center"
I run it, it shows up as running process. but it is not a graphic user interface and I can do little with command line

The camera light is on when "webcam" is running, yet I have no clue how to work with it.

Any idea ?

---

### Post by makeiteasy on 2011-05-17
I found and installed webcamstudio
Yet it doesn't seem you can upload picture or video to your own website. You have to chose one of provided ones, and have an account there.

CamStream worked as charm with hardy heron, it wont work now with Lucid.

Hopefully someone has the solution

---

### Post by makeiteasy on 2011-06-14
I am answering myself, maybe others will benefit.

camstream is working fine now, yet I have to open it from the command line using: LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camstream

If I close the command shell window, it closes camstream. so I keep it open.

I can use multiple webcams with it and upload to my site, Fun :)

Yet the video/picture quality is far from being good, one can say it is just working. In other OS , the video and picture quality are significantly better.

---

### Post by no2498 on 2011-06-14
you need to make this a bin file
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camstream

sorry i do not know how to do it
but have seen it in 1 of the skype ?'s here

---

