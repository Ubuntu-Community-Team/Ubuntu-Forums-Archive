---
title: "GIMP is resizing images really badly"
date: 2009-03-07
forum: Multimedia Software
---

### Post by svivian on 2009-03-07
I'm trying to shrink an image in GIMP but it keeps coming out really bad quality. It's a PNG but I've tried with BMP and JPG and get the same thing. The image is set to RGB colour mode so it's not that, and I've tried the different interpolcations (Linear, Cubic, Sinc) and I always get basically the same.

The original image:
[img]http://www.simpsoncrazy.com/content/games/jigsaws/indiana.png[/img]

GIMP's resize (left) compared to Paint Shop Pro (KolorPaint gives the same result as PSP):
[img]http://www.doheth.co.uk/files/gimp-resize.png[/img]

Does anyone else have this problem?

---

### Post by phpadik on 2009-03-07
GIMP works well for me? What version of GIMP are you using?

---

### Post by MickS on 2009-03-07
Seems OK with mine, cubic scale to 125 pixels wide if I'm reading it right.


Mick

---

### Post by svivian on 2009-03-07
I'm using the standard version of GIMP from the repo: 2.6.1-1ubuntu3

There must be something messed up with my version if it's working find for you guys. Any ideas of things to try?

---

### Post by Irony on 2009-03-07
Works with Sinc interpolation in Gimp 2.6.1 in Mepis 8.0

---

### Post by svivian on 2009-03-07
I just scaled the image using the Scale Tool and it works fine. But using the Image > Scale Image function, it messes up. I can't see any settings that are different. Why would these produce two vastly different images?

---

### Post by svivian on 2009-03-14
After some research it looks like the problem is a bug in 2.6.1 that should be fixed in the latest version. Does anyone know when GIMP will be updated in the repos? 2.6.5 is the latest stable version, released Feb 2nd. 2.6.1 was released back in October!

Alternatively, does anyone know if there are debs for the latest versions?

EDIT: found it: [http://www.getdeb.net/release/3814](http://www.getdeb.net/release/3814)
All is well.

---

### Post by Endolith on 2009-06-21
.

---

