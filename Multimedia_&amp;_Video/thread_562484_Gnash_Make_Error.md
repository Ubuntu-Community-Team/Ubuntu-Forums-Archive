---
title: "Gnash Make Error"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by aaaantoine on 2007-09-28
Gnash 0.8.1 won't build.  This is the error output (2>):

```
libtool: link: warning: `/usr/lib64/libjpeg.la' seems to be moved
libtool: link: warning: `/usr/lib64/libcurl.la' seems to be moved
libtool: link: warning: `/usr/lib64/libjpeg.la' seems to be moved
libtool: link: warning: `/usr/lib64/libcurl.la' seems to be moved
libtool: link: warning: `/usr/lib64/libxml2.la' seems to be moved
libtool: link: warning: `/usr/lib64/libfreetype.la' seems to be moved
libtool: link: warning: library `/usr/lib32/libSDL.la' was moved.
/usr/lib32/libSDL.so: could not read symbols: File in wrong format
collect2: ld returned 1 exit status
make[2]: *** [libgnashbackend.la] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
```

It appears that /usr/lib32/libSDL.so is the culprit here.  Is there a way to correct this?

---

