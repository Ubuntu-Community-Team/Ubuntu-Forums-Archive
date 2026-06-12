---
title: "Starting TV application (tvtime etc.) crashes X"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by scotty64 on 2007-11-26
I am having a hauppauge WinTV USB2 TV adapter. Whenever I try to start a TV application like tvtime X-windows crashes and I get the following backtrace in the xserver log:

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4ae6]
1: [0xffffe420]
2: /usr/bin/X [0x80c61c1]
3: /usr/lib/xorg/modules/extensions/libextmod.so(XvdiPutImage+0x159) [0xb7c70f64]
4: /usr/lib/xorg/modules/extensions/libextmod.so [0xb7c73c08]
5: /usr/bin/X(Dispatch+0x19e) [0x8085d86]
6: /usr/bin/X(main+0x47c) [0x806e108]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d48ea2]
8: /usr/bin/X(FontFileCompleteXLFD+0x8d) [0x806d671]

Fatal server error:
Caught signal 11.  Server aborting

I have attached my xorg.conf as file xorg.txt

Any ideas what is causing this problem ?

thanks Scotty

---

