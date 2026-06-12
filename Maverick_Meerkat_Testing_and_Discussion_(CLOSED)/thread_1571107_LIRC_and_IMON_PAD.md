---
title: "LIRC and IMON PAD"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by a-user on 2010-09-09
Well, i can't get my imonpad ir-control from my chiefteck hm01 working with maverick.

the lirc daemon starts. i don't have a /dev/lirc0 device or similar but the imon controlls apear in /dev/input/... as mouse and event_mouse input-devices, no ir device though.

the only ir-device i get is for my dvb-s haupaugue card wich i don't use.

thus lircd has no device to open.

i also tried the latest lirc (and modules) from the cvs (original lirc homepage).

---

### Post by a-user on 2010-09-10
/push. at least i would like to know if i there are others with this issue :(

---

### Post by cariboo on 2010-09-10
Have you created a bug about your problem?

---

### Post by mronkko on 2010-09-10
Also affecting me. Bug created


[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/635192](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/635192)

---

### Post by a-user on 2010-09-13
thx for the answers. no i hadn't time for it till now. but i see one already did so i will reply to it ti confirm it.

---

### Post by a-user on 2010-09-20
many updates till now but still no device for imon ir. release canditat shold come tomorrow. i wonder if this issue will be fixed. otherwise i have to stick with lucid although maverick fixed several other important things.

---

