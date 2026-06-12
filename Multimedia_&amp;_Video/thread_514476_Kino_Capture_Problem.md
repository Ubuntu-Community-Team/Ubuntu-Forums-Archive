---
title: "Kino Capture Problem"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by ryanVickers on 2007-07-31
Ok, I'm rying to capture video off my video camera using Kino.  When I plug it in to a firewire port and put the tape in and turn it on and hook it up and everything, I get the error:

> WARNING: dv1394 kernel module not loaded or failure to read/write /dev/dv1394/0

I've tryed running kino as root, switching "/dev/dv1394/0" to "/dev/dv1394-0", and looked around for help and no one seems to know how to fix it, or *thier *solution was to actually plug in the camera!  Please help!

FYI:
-my os: 7.04 64 bit
-AMD processor
-Asus A8V-E SE motherboard (didn't work with the gigabyte PRO-SLI or whatever one either)
-Sony Digital 8 Steadyshot camera (I think; I can't actually find the name!)

if you need more info just ask and I'll try!

---

### Post by Amazona aestiva on 2007-08-15
If you use 0.9.2(in Synaptic), I'll advise this:
[http://www.getdeb.net/download.php?release=872&fpos=0]("http://www.getdeb.net/download.php?release=872&fpos=0")

---

### Post by ryanVickers on 2007-08-15
Thanks!  I did have 0.9.3 and couldn't find a deb package on the kino site.

---

### Post by Amazona aestiva on 2007-08-15
It works correctly on my computer. It should work on yours too i think. ;)

---

### Post by Amazona aestiva on 2007-08-15
I have found this 1 minute ago!
[http://nakinub.noblogs.org/gallery/648/kino_1.1.1_i386.deb]("http://nakinub.noblogs.org/gallery/648/kino_1.1.1_i386.deb")
So I haven't tried it.

---

### Post by Amazona aestiva on 2007-08-15
WARNING!
Don't use 1.1.1 it isn't working. Sorry... good luck with 1.0.0;)

---

### Post by ryanVickers on 2007-08-17
1.0 didn't work.  I got this error:

```

(Reading database ... 197987 files and directories currently installed.)
Preparing to replace kino 0.92-1ubuntu3 (using .../kino_1.0.0-1~getdeb1_amd64.deb) ...
Document `kino-manual' is not installed, cannot remove.
Unpacking replacement kino ...
dpkg: error processing /home/ryan/Desktop/kino_1.0.0-1~getdeb1_amd64.deb (--install):
 trying to overwrite `/usr/lib/kino-gtk2/libkinoplus.so', which is also in package kinoplus
dpkg-deb: subprocess paste killed by signal (Broken pipe)


```

---

### Post by Amazona aestiva on 2007-08-20
Quite strange!
You should try this:[http://www.getdeb.net/app.php?name=Kino]("http://www.getdeb.net/app.php?name=Kino")
This is a new .deb package. It is working for me.;)

---

### Post by Amazona aestiva on 2007-08-20
And see what I wrote about there things:
[http://ubuntuforums.org/showthread.php?t=529759]("http://ubuntuforums.org/showthread.php?t=529759")

---

### Post by ryanVickers on 2007-08-20
Thanks, I got the 64 bit 1.1.1 to install.  I'll tell you how it goes!

---

### Post by ryanVickers on 2007-09-04
ok, it still won't capture, but I do like the new GUI! :)

p.s. sorry it took so long to try it out :(

---

