---
title: "Problem whit Skype Videochat."
date: 2012-12-22
forum: Multimedia Software
---

### Post by NahuelMS on 2012-12-22
Hello, apologies for my bad english.
I have a webcam genius facecam 1000, ubuntu 12.04, skype 4.1. I have problems whit videochating, i heard and see other people whi delay and whit slow motion. If i turn off the camara the situation goes better. When i turn on my webcam, the other can see me perfect but the screen start to twinklee whit blue, my web cam turn blue too, but the other still see me. If i left my webcam on but move the videochat windows putting my video window  out of the monitor screen the situation goes better but still wrong. I have been searching for weaks but seems that nobody else have this problem.I can see me perfect In the web cam preview in options and whit "webcam aplication". In cheese i have to move the window in order to start seying me in  the screen. In websites the webcam works good.

Bus 001 Device 003: ID 0458:707e KYE Systems Corp. (Mouse Systems) 

lsmod | grep videodev.
videodev               85626  1 uvcvideo

I think this webcam is incompatible whit V4l1 and uses V4l2. 

I already try to put the comand "bash -c "LD_PRELOAD=/usr/lib/libv4l/v4l2compat.so skype"" in the skype running access in aplication's menu but it didn't solve it.

Thanks a lot!!!!!!):P

---

