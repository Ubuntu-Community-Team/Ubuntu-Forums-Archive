---
title: "libproxychains.so.3 cannot be preloaded"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by yvsong on 2011-09-14
```
proxychains ping www.google.com
``` shows

ERROR: ld.so: object 'libproxychains.so.3' from LD_PRELOAD cannot be preloaded: ignored.

The library is in /usr/lib/. Any advice?

(2.6.38-11-generic x86_64 Ubuntu 11.04)

---

### Post by gmargo on 2011-09-14
This probably occurs since **/bin/ping** is a setuid-to-root binary.  What happens if you try **wget** or **curl**?

(Plus **proxychains** is meant for redirecting TCP, and ping doesn't use TCP.)

---

### Post by harshadsahasrabudhe on 2012-04-14
> **yvsong said:**
> ```
proxychains ping www.google.com
``` shows

ERROR: ld.so: object 'libproxychains.so.3' from LD_PRELOAD cannot be preloaded: ignored.

The library is in /usr/lib/. Any advice?

(2.6.38-11-generic x86_64 Ubuntu 11.04)

You can try downloading the i386 version of libproxychains.so.3 and placing it in /usr/lib32

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=593464](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=593464)

---

