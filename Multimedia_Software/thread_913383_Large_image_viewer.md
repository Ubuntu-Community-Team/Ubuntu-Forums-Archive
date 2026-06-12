---
title: "Large image viewer"
date: 2008-09-07
forum: Multimedia Software
---

### Post by ZioNemo on 2008-09-07
Hi,
I have a large (2.2G) geotif image I want to see.
What is the right application for that?
Apparently all applications I tried (including gimp, qgis, feh, eog, okular, ...) choke with that.

What can I use?

TiA
ZioNemo

---

### Post by lovinglinux on 2008-09-07
Do you need the geographic metadata or you just want to see the image?

I did some research and apparently you can convert the image to KML format using [GDal]("http://www.gdal.org/") and open it with Google Earth. The PRO version of Google Earth has native support for GEOTIFF, so you can open the image directly.

Unfortunately, I can provide a simple tutorial because I never used GIS tools and don't even have a GEOTIFF image to use as test sample.

If you need the geographic metadata you might want to consider reading this: [https://wiki.ubuntu.com/UbuntuGIS](https://wiki.ubuntu.com/UbuntuGIS)

---

