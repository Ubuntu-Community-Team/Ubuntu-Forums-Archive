---
title: "fglrx in dualhead mode"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by Semo on 2006-06-04
Hi,

I can't get dualhead to work with following configuration:
_ Two cards: (0/primary) PCI:Radeon 9250 and (1) AGP-4:Radeon 9550 Vivo; both are connected via DVI to LCD screens
_ X.org 7.0.0
_fglrx 8.25

works fine for only one card (0), but if I enable the second device (1) in xorg.conf X crashes like this:

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x86) [0x80b4a56]
1: [0xffffe420]
2: /usr/X11R6/bin/X(InitOutput+0x6b6) [0x809e097]
3: /usr/X11R6/bin/X(main+0x292) [0x806debe]
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d09ea2]
5: /usr/X11R6/bin/X(FontFileCompleteXLFD+0x81) [0x806d611]

Fatal server error:
Caught signal 11.  Server aborting

I attached xorg.conf and xorg.log.
Cand't figure out whats's wrong.](*,)  
Maybe someone is so kind to have a look at it.
Thanks a lot,

Semo

---

