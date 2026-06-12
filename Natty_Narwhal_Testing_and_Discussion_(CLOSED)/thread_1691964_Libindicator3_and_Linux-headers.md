---
title: "Libindicator3 and Linux-headers"
date: 2011-02-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Martin Marshalek on 2011-02-20
I just installed Natty Alpha 2 this morning and did a partial upgrade without thinking (I've since read the sticky though). Everything seems fine in fact, everything works better after the update, but I just want to make sure that this won't cause problems in the future. I read the dpkg-log and it seems that the partial upgrade only removed the linux-headers-2.6.38-1 package to install the linux-headers-2.6.38-4 package and the libindicator2 package to install the libindicator3 package. Is this all okay or do I need to mess with the packages to fix anything?

---

### Post by cariboo on 2011-02-20
If everything works, why mess with it. :) If you want to see what is being held back, open synaptic,, then clcik the status button in the lower left. Next clcik the update button, once it's finished click on upgradeable and click mark all upgrades and click apply, this will tell you what will be upgraded, removed or be unchanged.

---

### Post by Martin Marshalek on 2011-02-20
That's what I figured :) So far everything works pretty well, especially considering it's an alpha release. I've only had a few crashes and I'm very pleased with the way unity is going.

---

### Post by MadCow108 on 2011-02-20
old linux **headers** getting replaced is unproblematic. unlikely worst case is that some modules won't compile anymore (e.g. graphic drivers or virtualbox guest additions).

libindicator has got a new version and removed the old one:
[https://launchpad.net/ubuntu/natty/+source/libindicator/+changelog](https://launchpad.net/ubuntu/natty/+source/libindicator/+changelog)

this can cause problems as all dependencies need to be at least recompiled.
one which is does not work currently is unity-2d but this will get fixed soon.

---

