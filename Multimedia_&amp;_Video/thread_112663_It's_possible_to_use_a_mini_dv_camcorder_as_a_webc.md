---
title: "It's possible to use a mini dv camcorder as a webcam?"
date: 2006-01-04
forum: Multimedia &amp; Video
---

### Post by carlos.gil on 2006-01-04
I have a sony trv-22 camcorder, in windows i can use it as a webcam with the msn, so i was thinking if i could use it as a webcam with amsn.

It's possible to do this? or should i get a (real)webcam?

Thanks! 

Carlos Gil

---

### Post by damotor on 2006-07-19
I have the same isue with my jvc camcorder, the problem is that amsn and mercury use v4l and that camera is not supported, maybe in the next version of gaim...

---

### Post by leifharmsen on 2007-02-26
> **carlos.gil said:**
> I have a sony trv-22 camcorder, in windows i can use it as a webcam with the msn, so i was thinking if i could use it as a webcam with amsn.

It's possible to do this? or should i get a (real)webcam?

Thanks! 

Carlos Gil
This won't work for live video.  But if you just want to use your DV camera as a webcam here's a two line solution.  I'm using Ubuntu Edgy.  :

-make sure you have dvgrab and curl installed - I selected them with Synaptic Package Manager and they installed automatically.

Open your text editor and paste in this script:



#!/bin/bash

dvgrab --format jpeg --jpeg-overwrite --frames 1 --every 30 --jpeg-deinterlace --jpeg-width 640 --jpeg-height 480 --duration smpte=00:02 /home/leif/Desktop/webcam
                                                         
curl -T /home/leif/Desktop/webcam.jpg -u harmsen:**** [ftp://harmsen.net/images/webcam.jpg](ftp://harmsen.net/images/webcam.jpg)




Then make these changes to it
- change /home/leif/Desktop/ to the path to your Desktop (in both places in the script)
- change harmsen:**** to your ftp username:password
- change [ftp://harmsen.net/images/webcam.jpg](ftp://harmsen.net/images/webcam.jpg) to the place on your web host where you want your image to reside.

Run it and it should take a still from your dv camera, put it on your desktop and upload it to your website.  Put it in your /bin directory.  Use cron to schedule when you want it to take a snap, or put the commands in a timed loop using the sleep command.

---

### Post by damotor on 2007-04-11
[https://sourceforge.net/projects/dv2vloopback/](https://sourceforge.net/projects/dv2vloopback/)

---

### Post by coolcar on 2007-06-29
If its a Sony make sure that you take the Mini DV out else it will go to sleep after a set time

---

