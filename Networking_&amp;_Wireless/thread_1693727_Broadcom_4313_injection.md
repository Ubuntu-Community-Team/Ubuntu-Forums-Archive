---
title: "Broadcom 4313 injection"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by nash16 on 2011-02-23
Hi, I'm on Ubuntu 10.10 x86, my chipset is Broadcom 4313. I've downloaded the newest compat wireless drivers because I've read that these drivers are OK for injection with the new support for Broadcom 4313. I've applied the patches, but I can't make it, when I write in the console 'sudo make' I have some problems while it is building:

```
  CC [M]  /home/nano/Descargas/compat-wireless/drivers/net/wireless/rtlwifi/rtl8192ce/dm.o
/home/nano/Descargas/compat-wireless/drivers/net/wireless/rtlwifi/rtl8192ce/dm.c:38: fatal error: ../rtl8192c/dm_common.c: No existe el fichero o el directorio
compilation terminated.
make[5]: *** [/home/nano/Descargas/compat-wireless/drivers/net/wireless/rtlwifi/rtl8192ce/dm.o] Error 1
make[4]: *** [/home/nano/Descargas/compat-wireless/drivers/net/wireless/rtlwifi/rtl8192ce] Error 2
make[3]: *** [/home/nano/Descargas/compat-wireless/drivers/net/wireless/rtlwifi] Error 2
make[2]: *** [/home/nano/Descargas/compat-wireless/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/nano/Descargas/compat-wireless] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-2.6.35-25-generic»
make: *** [modules] Error 2
nano@NaNo:~$ 
```

I can't build it. I think that if I could install it, my chipset could seems OK to injection and with the Maxim patch I won't have any problems.


Thanks in advance!

---

