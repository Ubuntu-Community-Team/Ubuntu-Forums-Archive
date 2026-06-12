---
title: "Amarok's decided not to open"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by ensoriki on 2008-01-19
I try to open up amarok, I see the blue logo image but then thats it.
The logo disappears and no window opened up

So I tried to open it in terminal and got

$ amarok
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


What is that saying exactly?

---

### Post by kellemes on 2008-01-19
Is this helping?
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/172369](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/172369)

You could also try.. (but maybe you did already)
```

sudo apt-get remove --purge amarok
sudo apt-get install amarok

```

---

