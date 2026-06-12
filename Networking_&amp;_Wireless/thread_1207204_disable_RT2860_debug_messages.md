---
title: "disable RT2860 debug messages"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by prkfriryce on 2009-07-07
Is there a configuration parameter to disable the dmesg /var/adm/messages for the RT2860 driver:

os: Ubuntu 8.04.3 LTS  2.6.24-24-generic

driver: 2009_0521_RT2860_Linux_STA_V2.1.2.0

modinfo:
filename:       /lib/modules/2.6.24-24-generic/kernel/drivers/net/wireless/rt2860sta.ko
version:        2.1.2.0
license:        GPL

dmesg:

...
[312475.316783] MediaState is connected
[312475.316789] pAdapter->CommonCfg.Ssid=dlink , Ssidlen = 5
[312475.316794] ===>rt_ioctl_giwessid:: (Len=5, ssid=dlink...)
[312475.316801] ==>rt_ioctl_giwmode(mode=2)
[312475.316839] rt28xx_get_wireless_stats --->
[312475.316843] <--- rt28xx_get_wireless_stats
[312475.316882] ===>rt_ioctl_giwrange
[312476.315357] RT28xx_get_ether_stats --->
[312476.315808] ==>rt_ioctl_giwfreq  11
[312476.315818] MediaState is connected
[312476.315822] pAdapter->CommonCfg.Ssid=dlink , Ssidlen = 5
[312476.315824] ===>rt_ioctl_giwessid:: (Len=5, ssid=dlink...)
[312476.315828] ==>rt_ioctl_giwmode(mode=2)
[312476.315862] rt28xx_get_wireless_stats --->
[312476.315865] <--- rt28xx_get_wireless_stats
[312476.315901] ===>rt_ioctl_giwrange
[312477.315387] RT28xx_get_ether_stats --->
[312477.316099] ==>rt_ioctl_giwfreq  11
[312477.316264] MediaState is connected
[312477.316269] pAdapter->CommonCfg.Ssid=dlink , Ssidlen = 5
[312477.316271] ===>rt_ioctl_giwessid:: (Len=5, ssid=dlink...)
[312477.316742] ==>rt_ioctl_giwmode(mode=2)
[312477.316929] rt28xx_get_wireless_stats --->
[312477.316933] <--- rt28xx_get_wireless_stats
[312477.317261] ===>rt_ioctl_giwrange
[312478.313460] RT28xx_get_ether_stats --->
[312478.313877] ==>rt_ioctl_giwfreq  11
...

Thanks

---

### Post by prkfriryce on 2009-07-11
here's the source code:

[http://lxr.free-electrons.com/source/drivers/staging/rt2860/sta_ioctl.c](http://lxr.free-electrons.com/source/drivers/staging/rt2860/sta_ioctl.c)

I guess i could just wipe out some code, but i figured there would be a configuration parameter i could set after it's compiled.

---

