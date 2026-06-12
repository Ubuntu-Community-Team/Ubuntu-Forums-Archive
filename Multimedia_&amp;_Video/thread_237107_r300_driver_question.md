---
title: "r300 driver question"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by muchmusic on 2006-08-15
When I run glxinfo I get the message 

libGL error: dlopen /usr/X11R6/lib/modules/dri/r300_dri.so failed (/usr/X11R6/lib/modules/dri/r300_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: r300_dri.so

When I look for that driver, I find it in

/usr/lib/dri/r300_dri.so

only.

ldd /usr/X11R6/bin/glxinfo

gives me a bunch of links to /usr/lib instead of usr/x11 so I guess these are old links? I am new to this level of problem solving on linux

Everything else seems to be ok. What should I do?

---

