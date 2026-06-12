---
title: "Flash  DV Camera as webcam"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by Rocoso on 2007-02-18
Hi
Is there anyway to get my DV camera to work as a webcam?  To show up when using flash video applications.    My DV camera is working fine with kino.    
Thanks!

---

### Post by leifharmsen on 2007-02-26
> **Rocoso said:**
> Hi
Is there anyway to get my DV camera to work as a webcam?  To show up when using flash video applications.    My DV camera is working fine with kino.    
Thanks!
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

