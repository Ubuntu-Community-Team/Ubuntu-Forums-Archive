---
title: "git vlc libebml error"
date: 2010-11-02
forum: Multimedia Software
---

### Post by nokangaroo on 2010-11-02
I tried to compile vlc-git but I get an error "your libebml is too old". I downloaded libebml 1.0.0 but where does it go?

---

### Post by mc4man on 2010-11-02
> downloaded libebml 1.0.0 but where does it go?
Downloaded what?, a .deb(s), or the source.

If the source you'd need to build and install to /usr/local
(you may be able to build as static rather than shared/static

What you could try is dl'ing the maverick packages and installing, shouldn't be any conflict with the lucid, (I assume) version. (libebml0 in lucid and eariler, libebml2 in mav

If so, remove libebml-dev, but leave libebml0 installed.

Then go here, dl both libebml2 and libebml-dev for maverick, install either both at once or do libebml2 first, then the libebml-dev package

[http://packages.ubuntu.com/search?searchon=names&keywords=libebml](http://packages.ubuntu.com/search?searchon=names&keywords=libebml)

---

### Post by nokangaroo on 2010-11-02
Thanks! That solved my problem.

---

