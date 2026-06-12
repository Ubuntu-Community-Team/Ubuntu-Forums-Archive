---
title: "Kernel 2.6.30 Wired Network Problem"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by nn2004 on 2009-09-17
I upgraded to 2.6.30 the other day and lo and behold I have no wired networking. For some reason I cannot compile the ar81xx module. I will post the output of terminal so you can see.

```
nate@nate-laptop:~/Documents/src$ make install
make -C /lib/modules/2.6.30-02063003-generic/build SUBDIRS=/home/nate/Documents/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-02063003-generic'
  CC [M]  /home/nate/Documents/src/at_common_main.o
  CC [M]  /home/nate/Documents/src/atl1e_main.o
/home/nate/Documents/src/atl1e_main.c: In function ‘atl1e_request_irq’:
/home/nate/Documents/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
  CC [M]  /home/nate/Documents/src/atl1c_main.o
/home/nate/Documents/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/nate/Documents/src/atl1c_main.c:1635: error: expected expression before ‘;’ token
/home/nate/Documents/src/atl1c_main.c:1649: error: expected expression before ‘;’ token
/home/nate/Documents/src/atl1c_main.c:1673: error: expected expression before ‘;’ token
/home/nate/Documents/src/atl1c_main.c:1703: warning: ‘return’ with a value, in function returning void
/home/nate/Documents/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/nate/Documents/src/atl1c_main.c:2345: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/nate/Documents/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/nate/Documents/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-02063003-generic'
make: *** [default] Error 2


```


Any help regarding this topic would be greatly appreciated. Thank you.

---

### Post by robson9776 on 2009-09-19
I followed this instruction :

[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

and I got same problem with you... any clue, guys?

---

