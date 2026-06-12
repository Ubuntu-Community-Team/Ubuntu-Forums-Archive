---
title: "Squid3 - Has anyone managed to compile it successfully with SSL and SSL-CRTD enabled?"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by Khiron on 2012-04-09
I've been trying to compile squid 3.1.x with "--enable-ssl" and "--enable-ssl-crtd" but I keep getting errors related to squid_curtime in spite of applying the patch mentioned in [this]("http://bugs.squid-cache.org/show_bug.cgi?id=3263") bug report.

I'm currently running the 12.04 beta, but I tried to install it under 11.04 and 11.10 and I get the exact same error on squid_curtime. Perhaps I'm missing something.

First, I edit "debian/rules" and add "--enable-ssl" and "--enable-ssl-crtd". Save it, and then I run "debuild -us -uc -b". Here's the output I get with that:

```
../../lib/libmiscutil.a(MemPool.o): In function `MemPools::flushMeters()':
/root/sources/squid3-3.1.19/lib/MemPool.cc:224: undefined reference to `squid_curtime'
/root/sources/squid3-3.1.19/lib/MemPool.cc:225: undefined reference to `squid_curtime'
/root/sources/squid3-3.1.19/lib/MemPool.cc:223: undefined reference to `squid_curtime'
../../lib/libmiscutil.a(MemPoolChunked.o): In function `MemPoolChunked::deallocate(void*, bool)':
/root/sources/squid3-3.1.19/lib/MemPoolChunked.cc:357: undefined reference to `squid_curtime'
../../lib/libmiscutil.a(MemPoolChunked.o): In function `MemPoolChunked::convertFreeCacheToChunkFreeCache()':
/root/sources/squid3-3.1.19/lib/MemPoolChunked.cc:380: undefined reference to `squid_curtime'
../../lib/libmiscutil.a(MemPoolChunked.o):/root/sources/squid3-3.1.19/lib/MemPoolChunked.cc:406: more undefined references to `squid_curtime' follow
collect2: ld returned 1 exit status
make[4]: *** [ssl_crtd] Error 1
make[4]: Leaving directory `/root/sources/squid3-3.1.19/src/ssl'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/sources/squid3-3.1.19/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/sources/squid3-3.1.19/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/sources/squid3-3.1.19'
make: *** [debian/stamp-makefile-build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed
```

Which is the same error on the bug I linked before. Perhaps I'm not editing the right part? If I try to apply the patch, it does give me an error, but if I do it manually (which consists of editing the Makefile.am template, and possibly Makefile as well. Plus certificate_db.h) I still get the same error after redoing "debuild -us -uc -b".

Conversely, I've also tried to compile the beta builds of squid 3.2.x, which do compile successfully, but transparent (intercept) mode doesn't seem to work. All I get is a browser window stuck on "Waiting for response". So that won't work for now.

Anyone that has had success compiling it? What steps did you take?

---

