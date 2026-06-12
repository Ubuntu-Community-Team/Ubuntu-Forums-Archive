---
title: "Can't install lan card drivers"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by Sashin on 2009-08-11
I'm trying out the instructions on this page:
[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)

I get this

```
sashin@Laptop:~/src$ make
make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/sashin/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630-generic'
  CC [M]  /home/sashin/src/at_common_main.o
  CC [M]  /home/sashin/src/atl1e_main.o
/home/sashin/src/atl1e_main.c: In function ‘atl1e_request_irq’:
/home/sashin/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
  CC [M]  /home/sashin/src/atl1c_main.o
/home/sashin/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/sashin/src/atl1c_main.c:1635: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1649: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1673: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1703: warning: ‘return’ with a value, in function returning void
/home/sashin/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/sashin/src/atl1c_main.c:2345: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/sashin/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/sashin/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630-generic'
make: *** [default] Error 2
sashin@Laptop:~/src$ sudo make install
[sudo] password for sashin: 
make -C /lib/modules/2.6.30-020630-generic/build SUBDIRS=/home/sashin/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.30-020630-generic'
  CC [M]  /home/sashin/src/atl1c_main.o
/home/sashin/src/atl1c_main.c: In function ‘atl1c_intr’:
/home/sashin/src/atl1c_main.c:1635: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1649: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1673: error: expected expression before ‘;’ token
/home/sashin/src/atl1c_main.c:1703: warning: ‘return’ with a value, in function returning void
/home/sashin/src/atl1c_main.c: In function ‘atl1c_request_irq’:
/home/sashin/src/atl1c_main.c:2345: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/sashin/src/atl1c_main.o] Error 1
make[1]: *** [_module_/home/sashin/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.30-020630-generic'
make: *** [default] Error 2
```

---

### Post by chili555 on 2009-08-11
Please try:```
sudo apt-get install build-essential
```I am disappointed that a number of seemingly very helpful HOWTO's routinely neglect to tell us that there are prerequisites required before compiling from a tar.gz. All the prerequisites are included in the package, *build-essential*.

The tar.gz makes perfectly for me.

---

