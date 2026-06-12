---
title: "Error installing new gtkpod"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by shoofy on 2007-03-17
I'm trying to install an updated version of gtkpod, since the one in the Ubuntu repos is really out of date. I've tried installing both the latest released version and the latest CVS from source and the autogen.sh works fine, but when I run make it gave me this error at the end every time:
> /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpangoft2-1.0.so: undefined reference to `pango_quantize_line_geometry'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libpangoft2-1.0.so: undefined reference to `pango_font_describe_with_absolute_size'
collect2: ld returned 1 exit status
make[3]: *** [gtkpod] Error 1
make[3]: Leaving directory `/tmp/gtkpod/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/tmp/gtkpod/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/gtkpod'
make: *** [all] Error 2

I very much want to get this new version working, considering the amount of time I put into it already. I've looked all over to try to find a solution to this error and couldn't find one. Can anyone help?

---

