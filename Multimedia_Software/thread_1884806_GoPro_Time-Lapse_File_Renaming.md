---
title: "GoPro Time-Lapse File Renaming"
date: 2011-11-22
forum: Multimedia Software
---

### Post by KB1LQC on 2011-11-22
I just bought a GoPro HD camera and want to do some time-lapse photography with it. I am running into issues with ffmpeg regarding image order. It is not guaranteed that the images will start GOPR0001.JPG but could start on anything such as GOPR4441.JPG which causes ffmpeg to complain. I can't seem to find much regarding scripts to fix this for some reason. Maybe I am just searching the wrong terms? My scripting is very rusty, can anyone point me in the right direction to take a directory of a thousand images and rename them to start at GOPR0001.JPG and up?

FYI I am using the newest Ubuntu 11.10

---

### Post by FakeOutdoorsman on 2011-11-22
If they are already in sequential order, but not starting with 1, then you can try piping the images to ffmpeg from cat:
```
cat *.jpg | ffmpeg -f image2pipe -vcodec mjpeg -r 3 -i - -r 30 output.foo
```
Adjust input and output fps with the two -r options (in the example -r 3 is being applied to the input). You didn't specify a desired output format, so my example is fairly generic.

---

