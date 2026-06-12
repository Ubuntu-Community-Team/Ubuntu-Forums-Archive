---
title: "Amarok - bizzare problem"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by ibazulic on 2007-08-04
well, i've installed Ubuntu Edgy and updated it to Feisty via internet. and everything works perfectly :-) i also installed the original ATi drivers and i now have full OpenGL support...don't know if that is some part of the problem :-? 

well, here's the catch: i installed amarok using apt-get and installed all the necessary packages. and i can't run it. here's the error dump.

```

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

the first part i understand (i.e. i found what is the error), but i don't understand the second. it seems that amarok can't find libGL.so.1 but i have it on my computer:

```

ibazulic@confessor:~$ locate libGL.so.1
/usr/lib/xorg/FGL.renamed.libGL.so.1.2
/usr/lib/xorg/libGL.so.1.2
/usr/lib/xorg/libGL.so.1
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/lib/FGL.renamed.libGL.so.1.2
ibazulic@confessor:~$
```

so, what's the catch? why doesn't amarok see these libraries?

---

