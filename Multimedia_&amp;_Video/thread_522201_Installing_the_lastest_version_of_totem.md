---
title: "Installing the lastest version of totem"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by _Seven_ on 2007-08-10
I'm using ubuntu 7.04 and i would like to install the version 2.19.6 of totem. when i type the command ./configure appear a message that says that i need to have the gstreamer lib or the xine-lib. I already install both, the libgstreamer-dev and the lastest verison of xine-lib (1.1.7) but after this, the problem continues. What did i wrong?

Help me please.
Thanks =)

---

### Post by PaulFr on 2007-08-11
One possible cause: If you installed the latest versions of the gstreamer and xine-libs dev from source tar files, header files and libraries from these packages may be installed in /usr/local and not in the system standard places. You may need to specify where to find these headers and libraries when you run ./configure for the totem package. Run ```
./configure --help | more
``` and review the options you have.

---

### Post by nutz on 2007-08-11
[http://www.getautomatix.com/wiki/index.php?title=Main_Page](http://www.getautomatix.com/wiki/index.php?title=Main_Page)

---

