---
title: "IC100C webcam installation"
date: 2009-08-14
forum: Multimedia Software
---

### Post by merlin666 on 2009-08-14
I have a Micro Innovations IC100C webcam that I can not get to work. I found instructions at:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasMicroInnovations](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasMicroInnovations)

but this seems to be fairly outdated. I tried to patch a newer version of gspca, but this would not compile under Jaunty. Is there a way to add the camera specs to the gspca that is now built into jaunty? any other potential solutions?

---

### Post by merlin666 on 2009-08-26
bump - the lack of replies suggests that no one else uses an IC100C webcam with Ubuntu I guess.

---

### Post by Noreaster on 2010-02-10
> **merlin666 said:**
> bump - the lack of replies suggests that no one else uses an IC100C webcam with Ubuntu I guess.

Not true. I'm attempting to use the IC100C with Karmic. Did you have any luck? Thanks!

---

### Post by no2498 on 2010-02-10
try this
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each

get these 2 programs ( cheese ) you have in the repos
( wxcan ) get it from getdeb
1 or both will see your cam
cheese has a very nice help file look in its faq's
tells you how to stop the high cpu useage works on all cams

---

### Post by Noreaster on 2010-02-26
1. Went to gstreamer-properties and selected the cam.
2. Installed cheese. Can now see video, but it is very slow (and also bluish -- I guess I'll have to tweak that in cheese preferences).
3. Went to cheese Help and went back to gstreamer-properties and adjusted the output as recommended. No improvement, however. In addition, according to the System Monitor, there's not really any high CPU usage to speak of. All four processors are at 10% or less.

I have dual nVidia video cards (details below)... Does that change things any? I would imagine the answer is no. Again, I've already tried selecting that on gstreamer-properties, Video tab, Output area.

Quadro NVS 290 (GPU 0)
Quadro FX 1400 (GPU 1)

---

