---
title: "WARNING: erroneous pipeline: no element &quot;x264enc&quot;"
date: 2017-11-09
forum: Multimedia Software
---

### Post by ddc1996 on 2017-11-09
Hey i want to do the real time video transmission using G-streamer but am facing the error :-  WARNING: erroneous pipeline: no element "x264enc".
When i run the command :- 
gst-launch -e -v v4l2src device="/dev/video1" ! video/x-raw-yuv, framerate=25/1, width=640, height=360 ! \
   timeoverlay halign=right valign=bottom shaded-background=true ! \
   textoverlay text="Test Video 640x360 25fps" halign=left valign=bottom shaded-background=true ! \
   x264enc bitrate=498 ! mpegtsmux ! filesink location=video1.ts

Am Using Ubuntu 16.04 

Then i try to install :- sudo apt-get install gstreamer0.10-plugins-ugly-multiverse So Am getting error that :- 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gstreamer0.10-plugins-ugly-multiverse
E: Couldn't find any package by glob 'gstreamer0.10-plugins-ugly-multiverse'
E: Couldn't find any package by regex 'gstreamer0.10-plugins-ugly-multiverse'

So please help me to get rid of error :- erroneous pipeline: no element "x264enc" 
 
I have try my all the possible way but am not able to solve this error. Please help me ASAP .

Thanks,
Dhruv Desai

---

### Post by Yellow Pasque on 2017-11-09
It looks like you are trying to follow outdated advice. x264enc is found in gstreamer1.0-plugins-ugly
```
sudo apt-get install gstreamer1.0-plugins-ugly
```

---

