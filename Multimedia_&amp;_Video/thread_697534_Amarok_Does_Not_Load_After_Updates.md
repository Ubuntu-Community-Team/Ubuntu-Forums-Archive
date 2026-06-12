---
title: "Amarok Does Not Load After Updates"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by navneeth on 2008-02-15
A few days ago there were some updates for KDE (defintiely something to do with KDE, although I use Ubuntu). After a restart Amarok, which I've set as a start-up program, failed to load. After a few restarts, it still doesn't load. 

Here's the error message from terminal... 

```
navneeth@ubuntu:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libkutils.so.1: cannot open shared object file: No such file or directory

```

:confused:

---

### Post by navneeth on 2008-02-16
Customary bump!

---

