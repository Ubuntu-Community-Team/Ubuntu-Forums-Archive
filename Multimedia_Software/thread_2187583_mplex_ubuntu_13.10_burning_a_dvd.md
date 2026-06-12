---
title: "mplex ubuntu 13.10 burning a dvd"
date: 2013-11-12
forum: Multimedia Software
---

### Post by vanquishedangel on 2013-11-12
So after hours of searching and trying I came to a dead stop. I am trying to create and burn a movie file with brasero but I keep getting an error about mplex plugin not being installed. I have install gstreamer plugind bad and others like ubuntu restricted extras but no success. finally I got bombobo and so far it seems to be working, altho taking a long time.

I however hate redundancy and would like brasero to work for this task. Especially since it can be done through totem using brasero so I scoured the internet and found these articles:

[https://answers.launchpad.net/ubuntu/+source/brasero/+question/126918](https://answers.launchpad.net/ubuntu/+source/brasero/+question/126918)
[http://ubuntuforums.org/showthread.php?t=2147575](http://ubuntuforums.org/showthread.php?t=2147575)
[http://ubuntuforums.org/showthread.php?t=1523005](http://ubuntuforums.org/showthread.php?t=1523005)
[http://forums.linuxmint.com/viewtopic.php?f=47&t=139087](http://forums.linuxmint.com/viewtopic.php?f=47&t=139087)
[http://ubuntuforums.org/showthread.php?t=2162343&p=12813557#post12813557](http://ubuntuforums.org/showthread.php?t=2162343&p=12813557#post12813557)

I also read somewhere that the gstreamer-plugins-bad-multiverse in ubuntu 13.10 doest get built with mplex anymore??? :/ kinda disappointing, the multiarch doesnt have libSDL1.2.so.0 for 32bit either but that is another subject.

I however used catfish to search out mplex and I found that libmplex2-2.0-0 is located in usr/lib/x86_64-linux-gnu. So mplex seems to be there but not found? I hope there is a fix to this soon. If anyone has anyfixes tho please post them. I wonder if a symlink would solve this but I am not sure where brasero looks for mplex or by what name.

The actual error is:

All required applications and libraries are not installed. Please install the following manually and try again:
mplex (GStreamer plugin).

---

### Post by vanquishedangel on 2013-11-12
ok so I have come to the conclusion that brasero is broken, I used devede to creat the movie and it saved as an .iso and then I clicked burn, it crashed. I know totem uses brasero to write a movie to dvd as well, that failed tho because of mplex, devede doesnt require mplex though so I opened brasero. Brasero crashed when writing any .iso, I tried tinyxp.iso also and same thing. So I had to install xfburn. it is working.

So all those having issues with burning movies, the problem seems to be brasero, at least on my end.

---

### Post by Yellow Pasque on 2013-11-12
> **vanquishedangel said:**
> I however used catfish to search out mplex and I found that libmplex2-2.0-0 is located in usr/lib/x86_64-linux-gnu. So mplex seems to be there but not found?

mplex (or more accurately, libmjpegtools-dev package) needs to be present at build time. I filed a bug on it: [https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad1.0/+bug/1239029](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad1.0/+bug/1239029)

---

