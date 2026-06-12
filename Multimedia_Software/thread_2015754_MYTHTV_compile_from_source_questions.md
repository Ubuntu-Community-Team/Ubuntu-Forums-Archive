---
title: "MYTHTV compile from source questions"
date: 2012-07-03
forum: Multimedia Software
---

### Post by speed32219 on 2012-07-03
I have mythtv backend/frontend with ceton tuner working fine. I want to compile/install a frontend only on some of my atom based PC's. I download the Mythtv .25 tar ball and I was wondering how to compile with out mysql, xmltv and just basic frontend functionality. example: ./configure --disable-mysql --disable-xmltv ? 

I really only want the minimal install for a frontend, disk space restricted.

Note:  I'm not sure if I should use the tarball or use the git version.  I guess the git would have the latest fixes while the tarball would not?

---

### Post by BicyclerBoy on 2012-07-03
From memory use:
./configure --disable-backend

./configure --help

similarly can use disable-frontend option

I would (& do) use git (read only) to get 0.25+fixes (fixes/0.25) branch.
I think some of the tarballs are constructed daily (nightly).

---

### Post by speed32219 on 2012-07-03
Thank you for the quick reply.  That config line makes sense, no backend and not mysql either.  Thank you again

Downloading git version now. Thank you

---

### Post by BicyclerBoy on 2012-07-03
More than welcome...

Note you likely want to add some other options to that minimal configure example..
--proc-opt (or similar) might be good idea for low powered CPU.

---

