---
title: "Installation of Songbird on Ubuntu 10.10"
date: 2010-11-10
forum: Multimedia Software
---

### Post by chrissy.millichamp on 2010-11-10
How do you install songbird on Ubuntu 10.10, and whats the best webplayer?

---

### Post by aweber on 2010-11-28
Download from [https://wiki.songbirdnest.com/Developer/Articles/Builds/Contributed_Builds#Linux](https://wiki.songbirdnest.com/Developer/Articles/Builds/Contributed_Builds#Linux)

I got these errors
```
ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstaasink.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal
```

There is a related discussion at [http://ubuntuforums.org/showthread.php?t=1086378](http://ubuntuforums.org/showthread.php?t=1086378) (none of those worked for me) but just following the error message suggestion worked for me, so i ended up with 

```
./Songbird/songbird --gst-disable-segtrap
```

---

### Post by sikander3786 on 2010-11-28
Try this.

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

Source,

[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

---

