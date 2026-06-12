---
title: "Amarok crashing:  libGL.so"
date: 2008-08-04
forum: Multimedia Software
---

### Post by dogeatery on 2008-08-04
[http://ubuntuforums.org/showthread.php?t=583689](http://ubuntuforums.org/showthread.php?t=583689)

I'm having the same problem as the guy at the above link.  Amarok comes up with just a splash screen for a split second and then crashes.  My terminal output is the same as in the link:

```

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
 
```I have tried reinstalling mesa drivers and libGL.  It still doesn't work.  I had fiddled around with graphics drivers a while back to see if I could enable 3D on my Dell Inspiron 600m (with no-longer-supported graphics card).  I made sure to quit screwing around with important system files but maybe I messed something up after all?

FYI, I'm running Linux Mint Elyssa

---

### Post by dogeatery on 2008-08-23
bump?  :(

---

