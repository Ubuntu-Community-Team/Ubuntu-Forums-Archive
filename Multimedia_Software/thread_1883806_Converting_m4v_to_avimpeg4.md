---
title: "Converting m4v to avi/mpeg4"
date: 2011-11-19
forum: Multimedia Software
---

### Post by K-Jtan on 2011-11-19
Hi everyone,

A friend of mine asked me to burn on a DVD a few video that he bought, I guess, on iTunes. I have 2 problem. First one is I can't play the m4v on my computer (I tried totem/movie player and VLC and none of them work). So I believe I'm missing a library to read that file format. My second problem is I've tried to convert the video to something I could read and burn on a DVD since Devede won't recognise that format ether.

I've tried using winFF, no success, 

then I try to jump on command line using ffmpeg, 
```
ffmpeg -i input.m4v -target ntsc-dvd output.mpg
```no success, 

then I saw it's possible to use a command call mp4creator and do something like this : 
```
mp4creator -c temp_video.m4v -hint -r 30 output.mp4
```I can't how to install the library nor where to get it. It seem the project is called mpeg4ip and you should use 
```
sudo apt-get install mpeg4ip-server
```but this package seems to be down.

I ran out of ideas. I will appreciate any solution that will help me get progress on my second problem (I don't really care the first one, I don't need to watch the videos).

Thank you for your time
K-Jtan

---

### Post by hansdown on 2011-11-20
Hi, K-Jtan.

Try this.

[http://bdhacker.wordpress.com/2011/06/26/apple-ipod-iphone-video-converter-ubuntu/](http://bdhacker.wordpress.com/2011/06/26/apple-ipod-iphone-video-converter-ubuntu/)

---

### Post by cbowman57 on 2011-11-20
It's an mp4 file.  Do you have gstreamer0.10-plugins-base-apps installed?

Not sure if that has anything to do with it or not.

---

