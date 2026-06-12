---
title: "Can't install k3b"
date: 2008-10-14
forum: Multimedia Software
---

### Post by Kreuger on 2008-10-14
Hey people. First off I wanna say I don't even know how k3b got uninstalled but anyway I have some stuff to burn, vob files. Anyways, I went in to install some updates, this file libk3b3 and it keeps giving me an error:

> E: /var/cache/apt/archives/libk3b-dev_1.0.5-1ubuntu4~hardy1_i386.deb: trying to overwrite `/usr/lib/libk3b.so', which is also in package libk3b2 I've tried removing the file (libk3b3) and the .deb from the cache,  as well as using > sudo apt-get -f install and it won't work. Please help.

---

### Post by Kreuger on 2008-10-15
Anyone?

---

### Post by Archmage on 2008-10-15
How about removing libk3b**2**?

---

### Post by Kreuger on 2008-10-15
I tried that, it still gives the same error. When I tried upgrading it, it automatically marked libk3b2 for removal. Whenever I mark libk3b2 to be removed, it automatically marks libk3b3 to be installed and I guess it processes the libk3b3 first because it still fails.

Edit: I removed libk3b3 first, then libk3b2 and it let me reinstall k3b itself (along with libk3b3)

---

