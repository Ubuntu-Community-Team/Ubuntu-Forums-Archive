---
title: "64-bit libxine.so has no symbol 'gzopen64'"
date: 2010-02-05
forum: Multimedia Software
---

### Post by rlglende on 2010-02-05
I am running Ubuntu 9.10 on an x86_64 system.

xine worked until a recent update.  T

Now, xine fails for .avi, .wmv and .jpg files (at least), leaving the message:

xine: symbol lookup error: /usr/lib/libxine.so.1: undefined symbol: gzopen64

I uninstalled xine completely, reinstalled.  This didn't help.

'libxine' is /usr/lib/libxine.so.1.26.0.  File reports : libxine.so.1.26.0: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

I would un-install libxine.so, but doing this via synaptic also removes all of kde.

Suggestions?

Thanks.

---

