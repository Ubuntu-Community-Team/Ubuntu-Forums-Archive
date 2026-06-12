---
title: "Gstreamer and opengl - glimagesink"
date: 2009-01-11
forum: Multimedia Software
---

### Post by Haiyadragon on 2009-01-11
Hi. I want to use the opengl video output driver with gstreamer. However, the gstreamer0.10-gl package doesn't seem to be in the repo.

Does anyone know what package I have to install to get glimagesink to work?

---

### Post by zeroadhesion on 2010-04-29
Bump

---

### Post by no2498 on 2010-04-29
do you have the good,bad,and ugly installed ?

---

### Post by mc4man on 2010-04-29
Well there seems to be a long standing bug that isn't going anywhere
[https://bugs.launchpad.net/debian/+source/gstreamer0.10/+bug/227770](https://bugs.launchpad.net/debian/+source/gstreamer0.10/+bug/227770)

You could keep an eye on this ppa,  (or make a request there

[https://launchpad.net/~gstreamer-developers/+archive/ppa/+packages](https://launchpad.net/~gstreamer-developers/+archive/ppa/+packages)

Otherwise you could try sdl output 

**At your own risk** the plugin  is available in debian experimental
(I did install with no apparent ill effects on lucid
You need 2 packages, dl and install in this order

[http://packages.debian.org/experimental/libgstreamer-plugins-gl0.10-0](http://packages.debian.org/experimental/libgstreamer-plugins-gl0.10-0)
[http://packages.debian.org/experimental/gstreamer0.10-plugins-gl](http://packages.debian.org/experimental/gstreamer0.10-plugins-gl)

---

