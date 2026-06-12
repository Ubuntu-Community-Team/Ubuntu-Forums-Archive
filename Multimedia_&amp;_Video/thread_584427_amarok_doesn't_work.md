---
title: "amarok doesn't work"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by elnetotaca on 2007-10-21
this kindda sucks, now amarok don't work any more, this is the error;

userx@Hell:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
/usr/lib/amarok/amarokapp: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory
userx@Hell:~$

Anyone have any idea what can i do?

Neto.

---

### Post by catfacts on 2007-10-21
Install songbird. [http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

---

### Post by Whiffle on 2007-10-21
try

sudo apt-get -f install

sounds like you're missing some dependencies.

---

### Post by elnetotaca on 2007-10-21
i allready did it, and nothing, anyone know what can i do?

---

