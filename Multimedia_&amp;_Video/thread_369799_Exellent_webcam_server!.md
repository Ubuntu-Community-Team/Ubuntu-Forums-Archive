---
title: "Exellent webcam server!"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by arron on 2007-02-25
I thought I would post a excellent server application I have used for years for anyone else looking for a great easy to use application that is very stable.  Its called webcam_server not to be confused with the packaged webcam-server that i didn't find so easy to use.  I would recommend this over camserv and a couple other webam serving server applications I have tried to use.

The website is:

[http://webcamserver.sourceforge.net/](http://webcamserver.sourceforge.net/)

If you are looking for a awesome easy to run a webcam server this is it.  It is as easy as installing it and running:

webcam_server -p <port>  -s -d /dev/video0 -c "Look my webcam! %H:%M:%S"

It can use a config file.  I find the prompt very easy to run multiple webcams, all with different ports and a different text like:

webcam_server -p <port100>  -s -d /dev/video0 -c "Webcam 1 %H:%M:%S"
webcam_server -p <port101>  -s -d /dev/video1 -c "Webcam 2 %H:%M:%S"

It is very customizable and light on the system resources.  Worth haven a look if you are looking to serve up some webcams.

---

### Post by ulisse on 2007-12-30
Just tried on 7.10; it won't install because of some conflict with the "man1" folder position, but can be run from within the compiled source directory, and it works nice :)

It would be nice if somebody with better skills than mine would make a proper .deb

---

### Post by ulisse on 2007-12-30
hmm... actually I discovered that the packaged webcam-server is exactly the same of that other "webcam_server", so I dunno how you did found it more difficult to use :D

---

