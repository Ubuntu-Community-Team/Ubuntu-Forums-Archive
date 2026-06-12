---
title: "libgegl and libavcodec52"
date: 2010-02-26
forum: Multimedia Software
---

### Post by shendric on 2010-02-26
hey,

For some reason my GIMP install on Jaunty stopped being available.  When I tried to reinstall it, it says that it requires libgegl as one of the dependencies.  I can't seem to install libgegl, however, as I can only install libavcodec52 3:0.svn20090303 and it requires at least 3:0.svn200909091.  Does anyone know where I can get this version of libavcodec52, and why is there a GIMP release on synaptic that can't install because of the older versions of other packages?  Is there a repository that I don't have somewhere?

---

### Post by shendric on 2010-02-26
So, looking at the details for the libgegl-0.0-0 package for jaunty, I can't see any reason why there would be a dependency for libavcodec52.  The list of packages on [http://packages.ubuntu.com/jaunty/libgegl-0.0-0](http://packages.ubuntu.com/jaunty/libgegl-0.0-0) doesn't list that or libavcodec-unstripped-52 or libavformat52 for libavformat-unstripped-52, all of which apt says are required by libgegl-0.0-0.

Can anyone think of any reason why apt would require these packages for libgegl?  I'm really confused.

---

