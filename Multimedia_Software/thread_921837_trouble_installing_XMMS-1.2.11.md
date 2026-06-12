---
title: "trouble installing XMMS-1.2.11"
date: 2008-09-16
forum: Multimedia Software
---

### Post by zeelog on 2008-09-16
I'm not sure this is an Ubuntu problem, so much as an XMMS problem.
This is Ubuntu 8.04 and I'm trying to install XMMS-1.2.11 using the
old configure, make, make install method.
During configure, XMMS can not find glib-config.
The file just is not anywhere on Ubuntu 8.04 although I have installed
 libglib2.0-dev and libglib2.0-0
 /usr/lib/glib-2.0  is there along with all kinds of other glib stuff.
But there is no glib-config anywhere on Ubuntu 8.04.
 The error message from XMMS configure says to set the GLIB_CONFIG
environment variable to the full path of glib-config, but I can't do
that since there is no glib-config file on Ubuntu 8.04.
  Is there any way around this?  XMMS was always on Ubuntu before.
I like XMMS. It worked good. This time I have to install it myself
and its been one problem after another. Any information would be 
appreciated. Thanks!

---

### Post by markbuntu on 2008-09-16
You can just get the debs:

i386:

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

Change the output plugin to alsa and you should be good to go.

---

### Post by /usr/bin/hacked? on 2008-09-17
I was unable to divine any help out of those posts you listed. I still need to install libglib1.2. I have a 386, and I still am having trouble with libglib1.2.

---

### Post by zeelog on 2008-09-19
XMMS-1.2.11 is installed and works great! The .deb file worked with
no problems.  Thanks!

---

