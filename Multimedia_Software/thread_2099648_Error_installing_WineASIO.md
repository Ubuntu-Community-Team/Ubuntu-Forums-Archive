---
title: "Error installing WineASIO"
date: 2012-12-30
forum: Multimedia Software
---

### Post by iacoposk8 on 2012-12-30
Hello everyone! I'm trying to install WineASIO but I get an error:
```
make
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o asio.o asio.c
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o main.o main.c
gcc -c -I. -I/usr/include -I/usr/include -I/usr/include/wine -I/usr/include/wine/windows    -m32 -g -O2 -D__WINESRC__ -D_REENTRANT -fPIC -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wwrite-strings -Wpointer-arith -o regsvr.o regsvr.c
winegcc -shared -m32 wineasio.dll.spec -mnocygwin -L/usr/lib/wine -L/usr/lib -o wineasio.dll.so asio.o main.o regsvr.o     -ljack  -lodbc32 -lole32 -lwinmm -luuid
winegcc: gcc-4.5 failed
make: *** [wineasio.dll.so] Errore 2

```From what I understand not find the file: wineasio.dll.so
maybe it can be useful to this line:
```

locate wineasio.dll.so
/usr/lib/wine/wineasio.dll.so
```

---

