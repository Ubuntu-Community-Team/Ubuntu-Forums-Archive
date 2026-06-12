---
title: "Not sure if it belongs here but how do I upload video to my ubuntu pc from my..."
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by captain haddock on 2007-03-27
Samsung mini dv camcorder?
:confused:

---

### Post by fenian on 2007-03-27
First download kino...
> 
sudo apt-get install kino

Next make sure you have the proper modules enter in terminal...
> 
sudo lsmod | grep 1394
you  should see the modules ieee1394, ohci1394, raw1394, video1394, dv1394 listed if not enter in terminal...

> sudo modprobe [modulename]

replace modulename with the missing module name (i.e. , ieee1394)

Finally add read/write permission for user with the command...

> sudo chmod 0666 /dev/raw1394

You should now be able to use[ kino]("http://http://www.kinodv.org/article/static/2") to capture video.

---

### Post by macpointman on 2007-03-30
Every time I get something working in Ubuntu Linux I get one step closer to leaving Windows behind. 

Your post made a HUGE difference Now all I have to do is get my Camcorder to work as a Webcam with GYachE and I'll be almost set.  Thanks a bunch.

MacPointMan

---

