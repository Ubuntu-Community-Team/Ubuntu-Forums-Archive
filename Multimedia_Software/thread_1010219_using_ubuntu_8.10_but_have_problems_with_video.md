---
title: "using ubuntu 8.10 but have problems with video"
date: 2008-12-13
forum: Multimedia Software
---

### Post by TMachado on 2008-12-13
I've installed days ago Ubuntu 8.10 on my Toshiba A210-AC (on board ATI X1200). 

I'me using the recommended driver from Ubuntu, and compiz works fine (this info might be important). But when I run a video (mpg, divx, avi, even the effects from mp3), my screen "blinks". I dont know how to explain in English, but when I run those files my screen goes black and white very fast, that makes impossible to see anything. When I executed this files first time, I've installed the recommended drivers.

I've searched for better video drivers but I only found drivers to ATI X1250. 

Can you help me please? What could be the problem

---

### Post by Izek on 2008-12-13
go into Applications > Accessories > Terminal and type **gstreamer-properties** and hit enter. On the video tab, choose "X Window System (No xv)" under the plugin choice for the top section of the tab.

If it still continues, mind telling us what player you're using?

---

### Post by TMachado on 2008-12-13
> **Izek said:**
> go into Applications > Accessories > Terminal and type **gstreamer-properties** and hit enter. On the video tab, choose "X Window System (No xv)" under the plugin choice for the top section of the tab.

If it still continues, mind telling us what player you're using?

The problem exists wherever I use Totem or VLC... but well problem solved, but I have other problem now. there's seem to have a little "lag" when I play the video...

I dont know if this importante, but when I run gstreamer properties I have the following information:
tiago@tiago-laptop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'

---

### Post by TMachado on 2008-12-15
There's anyone can help me?

downloaded and installed oficial driver but same problem ...

I saw that is need a lot of packages pre installed, but I really dont know how to see if they are already installed... (see instalation instructions)

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by dk21 on 2009-01-05
I've the same exact problem. There are two more things that can be useful.

When I turn off compiz, video works fine.

Video runs slowly in fullscreen... Using Elisa Media Center it works better, but not perfectly...

Thanks in advance.

---

