---
title: "problems compiling ndiswrapper"
date: 2013-08-07
forum: Networking &amp; Wireless
---

### Post by npm1 on 2013-08-07
I am following section 4 of this web link:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

but when i type sudo make 
the following errors occur:

```
/home/****/Downloads/ndiswrapper-1.58/driver/loader.c: In function ‘load_user_space_driver’:
/home/****/Downloads/ndiswrapper-1.58/driver/loader.c:578:3: error: too few arguments to function ‘add_taint’
In file included from include/linux/cache.h:4:0,
                 from include/linux/time.h:4,
                 from include/linux/ktime.h:24,
                 from include/linux/timer.h:5,
                 from /home/****/Downloads/ndiswrapper-1.58/driver/ntoskernel.h:20,
                 from /home/****/Downloads/ndiswrapper-1.58/driver/ndis.h:19,
                 from /home/****/Downloads/ndiswrapper-1.58/driver/loader.c:16:
include/linux/kernel.h:404:13: note: declared here
make[3]: *** [/home/****/Downloads/ndiswrapper-1.58/driver/loader.o] Error 1
make[2]: *** [_module_/home/****/Downloads/ndiswrapper-1.58/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-3.10.5-031005-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/****/Downloads/ndiswrapper-1.58/driver'
make: *** [driver] Error 2


```

---

