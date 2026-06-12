---
title: "[SOLVED] HP Touchsmart"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by alight57 on 2008-12-12
I am trying to get the wireless network card working. It is a RALink. It comes up unclaimed. Any help would be appreciated.

adriaan@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:c6:db:fb:1a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.243 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:2e:30:f8:0d:0c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by alight57 on 2008-12-13
Found out that the HP Touchsmart uses the RALink 2790 chipset. the RT2860STA & RW Link software makes it work perfectly.

Thanks,

Adriaan

---

### Post by johnjohn2 on 2009-01-26
> **alight57 said:**
> Found out that the HP Touchsmart uses the RALink 2790 chipset. the RT2860STA & RW Link software makes it work perfectly.

Thanks,

Adriaan

How did you get it to work bro?

having the same issues

---

### Post by waspbr on 2009-01-26
you may be better off sending the dude above a private message or googling for it. since he's got only 2 post counts it doesn't seem he is around much.

---

