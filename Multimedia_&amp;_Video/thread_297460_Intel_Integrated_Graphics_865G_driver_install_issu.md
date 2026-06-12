---
title: "Intel Integrated Graphics: 865G driver install issues"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by happy-and-lost on 2006-11-11
I'm having some problems with installing Intel's official drivers for my onboard 856G graphics.

When I tar -xzvf the .tar.gz, cd to the xc directory it creates and try "make", it says to "make World". Fine. So I've "make World"ed and try make again, and after lots of complicated text it exists with...
```

/usr/include/X11/Xlib.h:3576: error: parameter name omitted
XAllowDv.c:71: error: &#8216;XExtDisplayInfo&#8217; undeclared (first use in this function)
XAllowDv.c:71: error: (Each undeclared identifier is reported only once
XAllowDv.c:71: error: for each function it appears in.)
XAllowDv.c:71: error: &#8216;info&#8217; undeclared (first use in this function)
XAllowDv.c:71: warning: implicit declaration of function &#8216;XInput_find_display&#8217;
XAllowDv.c:71: warning: nested extern declaration of &#8216;XInput_find_display&#8217;
XAllowDv.c:71: error: &#8216;dpy&#8217; undeclared (first use in this function)
XAllowDv.c:74: warning: implicit declaration of function &#8216;_XiCheckExtInit&#8217;
XAllowDv.c:74: warning: nested extern declaration of &#8216;_XiCheckExtInit&#8217;
XAllowDv.c:75: warning: return makes pointer from integer without a cast
XAllowDv.c:77: warning: implicit declaration of function &#8216;_XFlush&#8217;
XAllowDv.c:77: warning: nested extern declaration of &#8216;_XFlush&#8217;
XAllowDv.c:80: error: &#8216;dev&#8217; undeclared (first use in this function)
XAllowDv.c:81: error: &#8216;event_mode&#8217; undeclared (first use in this function)
XAllowDv.c:82: error: &#8216;time&#8217; undeclared (first use in this function)
make[3]: *** [XAllowDv.o] Error 1
make[3]: Leaving directory `/home/kjz/xc/lib/Xi'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/kjz/xc/lib'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/kjz/xc'
make: *** [all] Error 2

```

:confused:

---

