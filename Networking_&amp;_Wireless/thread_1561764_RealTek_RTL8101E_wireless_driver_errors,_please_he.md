---
title: "RealTek RTL8101E wireless driver errors, please help"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by gloria0227 on 2010-08-26
Hello,

I am trying to install the RealTek RTL8101E wireless driver and I get the following errors, does anyone know what they mean or how I can get wireless working?

```
Check old driver and unload it.
Build the module and install
/home/gloria/Downloads/r8101-1.018.00/src/r8101_n.c: In function ‘rtl8101_set_rx_mode’:
/home/gloria/Downloads/r8101-1.018.00/src/r8101_n.c:6892: error: ‘struct net_device’ has no member named ‘mc_count’
/home/gloria/Downloads/r8101-1.018.00/src/r8101_n.c:6901: error: ‘struct net_device’ has no member named ‘mc_list’
/home/gloria/Downloads/r8101-1.018.00/src/r8101_n.c:6901: error: ‘struct net_device’ has no member named ‘mc_count’
/home/gloria/Downloads/r8101-1.018.00/src/r8101_n.c:6902: error: dereferencing pointer to incomplete type
/home/gloria/Downloads/r8101-1.018.00/src/r8101_n.c:6903: error: dereferencing pointer to incomplete type
make[3]: *** [/home/gloria/Downloads/r8101-1.018.00/src/r8101_n.o] Error 1
make[2]: *** [_module_/home/gloria/Downloads/r8101-1.018.00/src] Error 2
make[1]: *** [modules] Error 2
make: *** [modules] Error 2
```


Thank you for your help,

Gloria

---

