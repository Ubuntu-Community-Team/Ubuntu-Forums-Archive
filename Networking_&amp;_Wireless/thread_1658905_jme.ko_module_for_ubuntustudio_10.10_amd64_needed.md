---
title: "jme.ko module for ubuntustudio 10.10 amd64 needed"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by hugocoolens on 2011-01-03
I have installed Ubuntustudio 10.10 amd64 on a machine which already runs Debian Squeeze (dual boot). Unfortunately when installing Ubuntustudio 10.10 amd64 the network card is not recognized, I know from my Debian Squeeze install I need a jme.ko module but as this is a different kernel I can't use the Debian Squeeze module. I tried to compile the module on the Ubuntustudio 10.10 system but I get the following errors as shown below. Anyone here knows how to solve this problem?

ilya@muziekdoos:~$ tar xvfj jme-1.0.5.tbz2 
jme-1.0.5/
jme-1.0.5/jme.c
jme-1.0.5/Makefile
jme-1.0.5/jme.h
ilya@muziekdoos:~$ cd jme-1.0.5/
ilya@muziekdoos:~/jme-1.0.5$ sudo -s
[sudo] password for ilya: 
root@muziekdoos:~/jme-1.0.5# ls
jme.c  jme.h  Makefile
root@muziekdoos:~/jme-1.0.5# make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/ilya/jme-1.0.5/jme.o
/home/ilya/jme-1.0.5/jme.c: In function ‘jme_set_multi’:
/home/ilya/jme-1.0.5/jme.c:2060: error: ‘struct net_device’ has no member named ‘mc_list’
/home/ilya/jme-1.0.5/jme.c:2061: error: ‘struct net_device’ has no member named ‘mc_count’
/home/ilya/jme-1.0.5/jme.c:2062: error: dereferencing pointer to incomplete type
/home/ilya/jme-1.0.5/jme.c:2064: error: dereferencing pointer to incomplete type
make[2]: *** [/home/ilya/jme-1.0.5/jme.o] Error 1
make[1]: *** [_module_/home/ilya/jme-1.0.5] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [all] Error 2

---

