---
title: "How to enable IPv6 support?"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by klikli on 2010-12-26
Don't tell me it's enabled by default. It's a trimmed version of Ubuntu 9.04 ARM build.

```
root@debian:/# ifconfig
eth0      Link encap:Ethernet  HWaddr f0:ad:4e:00:35:5a
          inet addr:172.28.1.3  Bcast:172.28.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14605 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:532
          RX bytes:16986022 (16.9 MB)  TX bytes:1091919 (1.0 MB)
          Interrupt:11

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

When I tried to enable it, I failed.
```
root@debian:/# modprobe ipv6
FATAL: Could not load /lib/modules/2.6.22.18/modules.dep: No such file or directory
```

I tried to download the Kernel source, but I can hardly choose which one should I download.

```
root@debian:/# apt-cache search linux-image
alsa-base - ALSA driver configuration files
linux-image-2.6.28-11-imx51 - Linux kernel image for version 2.6.28 on I.MX51-based systems
linux-image-2.6.28-11-iop32x - Linux kernel image for version 2.6.28 on IOP32x-based systems
linux-image-2.6.28-11-ixp4xx - Linux kernel image for version 2.6.28 on IXP4xx-based systems
linux-image-2.6.28-11-versatile - Linux kernel image for version 2.6.28 on Versatile-based systems
linux-image-imx51 - Linux kernel image for version 2.6.28 on I.MX51-based systems
linux-image-iop32x - IOP32x-based systems Linux kernel image
linux-image-ixp4xx - IXP4xx-based systems Linux kernel image
linux-image-versatile - Versatile-based systems systems Linux kernel image
rt2400-source - source for rt2400 wireless network driver
rt2500-source - source for rt2500 wireless network driver
rt2570-source - source for rt2570 wireless network driver

```


Currently I'm on:
```
root@debian:/# uname -a
Linux debian 2.6.22.18 #1 Thu Mar 19 14:46:22 IST 2009 armv5tejl GNU/Linux
```

---

### Post by hugmenot on 2010-12-26
It&#8217;s definitely enabled by default in a later version than 9.04. Is upgrading a possibility?

---

