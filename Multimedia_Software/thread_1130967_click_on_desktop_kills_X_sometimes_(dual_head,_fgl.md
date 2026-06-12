---
title: "click on desktop kills X sometimes (dual head, fglrx)"
date: 2009-04-20
forum: Multimedia Software
---

### Post by ostrm on 2009-04-20
Hi,

this is a pretty bizarre one...

I've just set up dual head display using fglrx and everything seems fine besides random X restarts due to an fglrx crash. This happens only when the desktop is clicked (wtf?) on the *second* display and after a random number of preceding clicks. 

This is the relevant backtrace from Xorg.log:
```
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3019]
1: [0xb80e0400]
2: /usr/lib/dri/fglrx_dri.so [0xb481b3ec]
3: /usr/lib/dri/fglrx_dri.so [0xb490931c]
4: /usr/lib/dri/fglrx_dri.so [0xb47d6bc5]
5: /usr/lib/dri/fglrx_dri.so [0xb47d71ad]
6: /usr/lib/dri/fglrx_dri.so [0xb436f618]
7: /usr/lib/dri/fglrx_dri.so [0xb4573cd5]
8: /usr/lib/xorg/modules/extensions//libglx.so [0xb7bdaf5e]
9: /usr/lib/xorg/modules/extensions//libglx.so [0xb7bd8b26]
10: /usr/lib/xorg/modules/extensions//libglx.so [0xb7bd8d08]
11: /usr/lib/xorg/modules/extensions//libglx.so [0xb7bdcfe8]
12: /usr/X11R6/bin/X(Dispatch+0x34f) [0x808c89f]
13: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
14: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ce2685]
15: /usr/X11R6/bin/X [0x8071101]
Saw signal 8.  Server aborting.

```

I'm on a Thinkpad T60, ATI X1300, fglrx driver, first screen: 1440x1050, second screen 1028x1024, big desktop setup.

Anyone experienced the same? Any ideas?

---

### Post by markbuntu on 2009-04-20
I think there was a comment about that in the release notes for one of those fglrx drivers. Which one are you using?

---

