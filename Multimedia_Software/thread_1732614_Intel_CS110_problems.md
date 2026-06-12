---
title: "Intel CS110 problems"
date: 2011-04-18
forum: Multimedia Software
---

### Post by cbennett926 on 2011-04-18
Ok, I am currently running Lucid 10.04 Ubuntu through Wubi and am having MAJOR problems with my webcam. I can use this webcam on windows vista without a problem and very nice picture quality, but when I try and use it on Ubuntu I run into some snags. The webcam is connected and works, kind of, on "cheese", but when I run a test on skype it is just a black box. 
 
I have found some code through the forums that allows me to run skype via terminal and will let my webcam work as well as it will on Cheese. Now, when it does run the picture is very blue and dark as well as extremely laggy compared to when ran on Windows Vista.

---

### Post by BicyclerBoy on 2011-04-18
As your webcam kind-of-works.. I would suggest you try 
guvcview

Cheese just does not compare..

guvcview is lot more configurable (brightness, contrast etc) & faster..

Could you post the cmd line you use to launch the webcam with skype ?

---

### Post by cbennett926 on 2011-04-19
#!/bin/bash
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

---

### Post by BicyclerBoy on 2011-04-20
AFAIK that loads the legacy v4l library & not v4l2 mode..

You can do the same with gstreamer-properties config & guvcview..

This is a good webcam link..
[https://wiki.archlinux.org/index.php/Webcam_Setup](https://wiki.archlinux.org/index.php/Webcam_Setup)

---

### Post by cbennett926 on 2011-04-20
how can I get it to use the v4l2? Also, is there a way I can enhance the video quality? Is it Skype's problem, ubuntu's, or mine?

---

