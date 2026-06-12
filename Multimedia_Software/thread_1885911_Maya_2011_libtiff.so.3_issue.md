---
title: "Maya 2011: libtiff.so.3 issue"
date: 2011-11-24
forum: Multimedia Software
---

### Post by Corporation on 2011-11-24
So, I have Ubuntu 11.10 installed, and I followed [_this guide_]("http://etoia.free.fr/?p=1611") to get Maya installed on it, but now I cannot launch Maya because I get this error:

/usr/autodesk/maya2011-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

When I look in /usr/lib, there are no libtiff.so.* files at all, and symlinking the one in /usr/lib32 does nothing to aid the opening.

I believe Maya is 64 bit. How do I install libtiff on 64 bit?

---

### Post by Jahid65 on 2011-11-24
have you installed libtiff3 or libtiff4 (64 bit, if any) & libtiff-devel??? if you don't have libtiff3, then you may need to soft link it with libtiff4.
```

sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

btw I don't use Ubuntu now. Doesn't it has libtiff4 64 bit version?? Opensuse has it.

---

### Post by Corporation on 2011-11-24
Thanks for your reply.

I have libtiff4 installed, libtiff3 and libtiff-devel show nothing in apt.

There is nothing in /usr/lib/ called libtiff.*, only in /usr/lib32, which as previously mentioned did not work when I symlinked it to /usr/lib/libtiff.so.3 or /usr/lib32/libtiff.so.3.

To me, this suggests that Maya wants the 64-bit libtiff.

I've managed to solve this issue, had to do the following:

sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 /usr/lib/libtiff.so.3

---

