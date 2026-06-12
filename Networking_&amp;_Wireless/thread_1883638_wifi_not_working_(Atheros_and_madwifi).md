---
title: "wifi not working (Atheros and madwifi)"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by mark1977 on 2011-11-19
Hi,

I can't get my wifi working. I'm running Ubuntu 10.04 and as far as I know have a Atheros Communications Inc. Network Controller, which I understand you need the madwifi drivers for. So I followed this post [http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781) and (presumably) installed the drivers, though to be honest I don't know how to check if a driver is installed. When I run lshw -C network, it doesn't seem that there is a driver installed.

Any help gratefully appreciated :)

Below is some useful output:

```
mark@kapu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: b8:70:f4:66:0a:01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.67 latency=0 multicast=yes
       resources: irq:26 ioport:3000(size=256) memory:d0404000-d0404fff(prefetchable) memory:d0400000-d0403fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d1500000-d151ffff memory:d0d00000-d0d0ffff(prefetchable)

```

lsmod

```
mark@kapu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: b8:70:f4:66:0a:01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.67 latency=0 multicast=yes
       resources: irq:26 ioport:3000(size=256) memory:d0404000-d0404fff(prefetchable) memory:d0400000-d0403fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d1500000-d151ffff memory:d0d00000-d0d0ffff(prefetchable)

```

```
mark@kapu:~$ sudo rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
```

```
mark@kapu:~$ sudo rmmod ath5k
ERROR: Module ath5k does not exist in /proc/modules
```


```
mark@kapu:~$ sudo rmmod ath_hal
mark@kapu:~$
```

```
mark@kapu:~$ sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```

```

mark@kapu:~$ sudo modprobe ath5k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```


```
mark@kapu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: b8:70:f4:66:0a:01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.67 latency=0 multicast=yes
       resources: irq:26 ioport:3000(size=256) memory:d0404000-d0404fff(prefetchable) memory:d0400000-d0403fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d1500000-d151ffff memory:d0d00000-d0d0ffff(prefetchable)

```

```
mark@kapu:~$ dmesg | grep -e ath -e wlan
[    1.349379] device-mapper: multipath: version 1.1.0 loaded
[    1.349381] device-mapper: multipath round-robin: version 1.0.0 loaded

```

Thanks!

Mark

---

