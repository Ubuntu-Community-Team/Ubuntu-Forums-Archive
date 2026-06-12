---
title: "Wireless Drivers Doesnt Work on Ubuntu    running HP Pavillion dv5z-1000"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by hacker0wnz on 2008-12-06
I need Help Please My Wireless Doesnt Seem To Work.

I checked the on the Hardware Drivers It Says Activated but It Also says In Use.

Help Please.

---

### Post by Ayuthia on 2008-12-06
Can you go into the Terminal and post the results of:
```
lshw -C network
```
If it is a Broadcom card, can to tell us which option you selected from Hardware Drivers?

---

### Post by hacker0wnz on 2008-12-06
okay i did that on terminal and i get this codes





```
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:cb:ed:f2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:97:b3:44:12:d5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```


And The Driver Is Atheros 802.11 wireless LAN cards


help please.




Thanks.

---

