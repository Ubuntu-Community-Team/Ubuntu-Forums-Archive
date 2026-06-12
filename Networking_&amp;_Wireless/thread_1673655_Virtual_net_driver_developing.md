---
title: "Virtual net driver developing"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by Strell on 2011-01-22
Hi Everyone!

I just started to develop net driver and I have a problem.

I tried to compile existing driver, that i have found in linux kernel sources (drivers/net/dummy.c) and i have a lot of errors.

I have investigate this, and i have found that errors appears when i try to use netdevice.h header file. :(
```

/development/projects/kernel/linux-2.6.37/include/linux/if.h:177: error: field ‘ifru_addr’ has incomplete type
/development/projects/kernel/linux-2.6.37/include/linux/if.h:178: error: field ‘ifru_dstaddr’ has incomplete type
/development/projects/kernel/linux-2.6.37/include/linux/if.h:179: error: field ‘ifru_broadaddr’ has incomplete type
/development/projects/kernel/linux-2.6.37/include/linux/if.h:180: error: field ‘ifru_netmask’ has incomplete type
/development/projects/kernel/linux-2.6.37/include/linux/if.h:181: error: field ‘ifru_hwaddr’ has incomplete type

```

Does anybody known what is a problem?

Thanks.

---

