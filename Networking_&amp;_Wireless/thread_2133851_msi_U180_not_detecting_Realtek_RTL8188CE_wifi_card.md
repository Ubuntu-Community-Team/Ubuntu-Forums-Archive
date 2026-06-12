---
title: "msi U180 not detecting Realtek RTL8188CE wifi card"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by saulusoc on 2013-04-09
hi, total beginner here who is totally unhappy with windows and had ubuntu loaded on an old laptop for me.
just got a msi u180 and all ios working fine except i have no wifi, even when i turn on and off the card using the Fn F11 function.
can anyone help please?

---

### Post by sandyd on 2013-04-09
Welcome to Ubuntu :)

Can you open a terminal (Unity Dash -> Type in Terminal), and post the output of the following commands.

```

lspci
lsusb
sudo lshw -C NETWORK

```
Thanks.

---

### Post by saulusoc on 2013-04-09
hi, thanks for the quick reply
got this back

No command 'spci' found, did you mean:
 Command 'sci' from package 'scheme2c' (universe)
 Command 'spc' from package 'supercat' (universe)
 Command 's2ci' from package 'scheme2c' (universe)
 Command 'xpci' from package 'xdiagnose' (main)
 Command 'lspci' from package 'pciutils' (main)
spci: command not found
paul@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
paul@ubuntu:~$ sudo lshw -C NETWORK

---

### Post by saulusoc on 2013-04-09
sorry, didn't look right and did again and got this

 ```
*-network               
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rtl8192ce latency=0
       resources: irq:16 ioport:e000(size=256) memory:dfe00000-dfe03fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: 8c:89:a5:05:eb:51
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.24 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:dfd04000-dfd04fff memory:dfd00000-dfd03fff
```

---

### Post by sandyd on 2013-04-09
Hmm
a bit buggy I see.
The card doesn't work at the moment.

see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557)

---

