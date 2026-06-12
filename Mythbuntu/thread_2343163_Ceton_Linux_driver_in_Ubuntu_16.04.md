---
title: "Ceton Linux driver in Ubuntu 16.04"
date: 2016-11-14
forum: Mythbuntu
---

### Post by Karl_Shea on 2016-11-14
These are the changes to get the Ceton Linux driver working in 16.04 (See [thread]2291607[/thread] for more information)

Add **-Wno-error=date-time** to both **EXTRA_CFLAGS** sections in the Makefile (or, presumably, check the code out from [https://github.com/ceton/infinitv_pcie](https://github.com/ceton/infinitv_pcie) where it looks like that error was fixed)

If you need to keep the ctn0 interface name, add a file called **99-ceton.link **to **/etc/systemd/network**

```
[Match]
Driver=ctn91xx


[Link]
Name=ctn0
```

---

