---
title: "installing patch to fix myth aspect"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by canzi on 2007-11-14
Hi Guys n Gals

how does one apply apply a patch from Track?

aspectRatio-0-20-2.a.patch
see [http://svn.mythtv.org/trac/ticket/2581]("http://svn.mythtv.org/trac/ticket/2581")

Id also be interested if anyone knows how to crop pillars with nuvexport

any help greatly appreciated

cheers

Steve

---

### Post by canzi on 2007-11-15
needs to be done via svn

svn co [http://svn.mythtv.org/svn/branches/release-0-20-fixes/mythtv](http://svn.mythtv.org/svn/branches/release-0-20-fixes/mythtv)
cd mythtv
wget [http://svn.mythtv.org/trac/raw-attachment/ticket/2581/aspectRatio-0-20-2.a.patch](http://svn.mythtv.org/trac/raw-attachment/ticket/2581/aspectRatio-0-20-2.a.patch)
patch -p0 < aspectRatio-0-20-2.a.patch

---

