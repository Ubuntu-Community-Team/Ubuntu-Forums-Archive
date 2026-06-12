---
title: "spca5xx driver - can resolution be configured?"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by Mike_SMD on 2006-11-15
Hi everyone,
I'm a linux newbie but I just got my logitech webcam working with the spca5xx driver. However, it seems that the resolution is a little bit under what the specs on the box said the camera should be capable of giving. Does anyone know how I go about configuring the driver to give me the proper performance? Is this possible, perhaps using some utility or editing a config file?

I've been looking, but the web is a *biiiiiiig* place and most of it seems to be in french.

Which doesn't much help.

All efforts appreciated!


Thanks,

Mike_SMD

---

### Post by RFScheer on 2006-11-16
I haven't been able to get mine working yet - Logitech Quickcam Pro 5000.  

I'll let you know if I figure it out.  What model is yours?

---

### Post by RFScheer on 2006-11-17
Success with Quickcam Pro 5000 on Edgy AMD64 !!!

Get the uvcvideo driver source:

[http://people.via.ecp.fr/~flo/debian/pool/main/linux-uvc/linux-uvc_0.0.0.svn20061002.orig.tar.gz](http://people.via.ecp.fr/~flo/debian/pool/main/linux-uvc/linux-uvc_0.0.0.svn20061002.orig.tar.gz)

Extract it, cd into the extracted directory, make, sudo make install...easy.

Get this viewer - luvcview:

[http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060920.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20060920.tar.gz)

Make sure you have installed the libsdl packages, including -devs from ubuntu edgy repos.

Extract the luvcview gz file, cd into the new directory, make, sudo make install....easy.

Now load the new driver module:  sudo modprobe uvcvideo

Check to make sure your cam is jacked in.  

Launch luvcview with:  luvcview -d /dev/video0 -L 

And you're golden!

It also works with ekiga but I only verified video and don't use it otherwise.

Does not work with camorama.  

Now, the hard work of developing vision for a RoboMagellan bot.

---

