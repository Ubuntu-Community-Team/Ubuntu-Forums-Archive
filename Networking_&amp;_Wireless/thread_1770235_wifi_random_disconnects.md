---
title: "wifi random disconnects"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by gian on 2011-05-28
hello All,

I am experiencing very frequent disconnects && auto reconnects on my notebook, but somehow I found that if I shutdown the pc, remove the battery, count to 30, insert the battery and reboot, it will ne rock solid working perfectly... until next reboot.

Before I try to provide evidence to what I'm saying, I'm asking here if there is a reasonable explanation of this behavior. 

thanks for reading,
ciao,
-Gian

---

### Post by garvinrick4 on 2011-05-29
Most all the time it is a driver problem. List your cards and see if anyone knows the fix. 
I have to run my intel 1000 only in g because the driver iwlagn slows, disconnects and such when
running N in my router. Have other operating systems that will run at N so do not want to set
router at g speeds. There ended up being a one line config file fix to drop the n from my card.
In other words run this and post might get some help. (Long story to say that Huh)
```
sudo lshw -C network
```

---

### Post by gian on 2011-05-29
if it was a driver problem it would diconnect all the time, or would not reconnect automatically.

however, here it is:

  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:af:5f:ea
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:bc00(size=256) memory:d0200000-d0200fff memory:d0000000-d0003fff memory:d0020000-d003ffff
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: c0:cb:38:7b:f3:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192CE driverversion=0005.1116.2010 firmware=56 ip=192.168.2.54 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:10 ioport:c000(size=256) memory:d0600000-d0603fff

---

### Post by garvinrick4 on 2011-05-29
Looks like is in a ppa as of about 13 weeks ago. Bug first link and PPA second link for your driver.


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/686333](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/686333)

[https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)

---

