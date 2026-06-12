---
title: "recordmydesktop problem"
date: 2009-05-05
forum: Multimedia Software
---

### Post by gbstack on 2009-05-05
I ran the recordmydesktop in the terminal,then clicked a link in a web site,next I pressed Ctrl-C in the terminal,recordmydesktop doesn't work...:(

But if I only stayed on the desktop for minutes and then press Ctrl-C in the terminal,recordmydesktop works!

error message:
```
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a62767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7a628b1]
#2 /usr/lib/libX11.so.6 [0xb7ebb421]
#3 recordmydesktop [0x804b174]
#4 recordmydesktop [0x8051083]
#5 recordmydesktop [0x804f21c]
#6 /lib/tls/i686/cmov/libpthread.so.0 [0xb7d814fb]
#7 /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7b3ae5e]
```


what's the matter with my recordmydesktop?

anyone can help me?

---

### Post by gbstack on 2009-05-06
sometimes it does work,but sometimes it doesn't work.:(

anyone can help me?

---

