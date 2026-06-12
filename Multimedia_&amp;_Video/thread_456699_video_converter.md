---
title: "video converter"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by md5hash on 2007-05-28
is there a video converter for ubuntu with gui support.?

---

### Post by endersshadow on 2007-05-28
Woohoo, shameless plug time!

[http://vive.sourceforge.net](http://vive.sourceforge.net)

I'd recommend the SVN checkout, but you can use whatever you feel most comfortable with.

Full disclosure: It's my program.

Other programs (in the repos): AcidRip, GMencoder

---

### Post by md5hash on 2007-05-28
thanks alot. ill try

---

### Post by martinitime1975 on 2008-01-16
I have added the mediabuntu repositories and I'm still getting dependency issues:

bjoiner@linuxbox:/temp$ sudo dpkg -i vive_2.0.0-0ubuntu1_i386.deb
Selecting previously deselected package vive.
(Reading database ... 164068 files and directories currently installed.)
Unpacking vive (from vive_2.0.0-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of vive:
 vive depends on libavcodec0d (>= 0.cvs20060823); however:
  Package libavcodec0d is not installed.
 vive depends on libavformat0d (>= 0.cvs20060823); however:
  Package libavformat0d is not installed.
 vive depends on libavformat0d; however:
  Package libavformat0d is not installed.
dpkg: error processing vive (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vive

I've done the apt-get -f install and all that.  What am I missing?

---

