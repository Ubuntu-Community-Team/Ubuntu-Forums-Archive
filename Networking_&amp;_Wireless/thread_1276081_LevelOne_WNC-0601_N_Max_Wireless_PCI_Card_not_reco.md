---
title: "LevelOne WNC-0601 N_Max Wireless PCI Card not recognized"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by sammm on 2009-09-26
Hi,
I just bought this new wireless card. I know I should have first checked if it is supported. The card seems to work, the blue led lights up.

The card does not seem to be recognized by my system (Jaunty 9.04).
It is not listed on any wireless list I found on the internet,
although the WNC-0301 card has been reported to work.
Could anybody suggest the steps I should take to make this thing work?
Thanks in advance.

lspci: no wireless reported
ifconfig: idem
iwconfig: idem
lsmod: idem
dmesg: see attachment
```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth4
       version: 02
       serial: 00:24:21:2b:59:1b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:0a:4a:70:91:55
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
iwlist scan: no interface that supports scanning
uname -mr: 2.6.28-15-generic i686
sudo /etc/init.d/networking restart:
 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth4=eth4.
(eth4 is the wired network)

sudo pccardctl ident: no output

---

### Post by sammm on 2009-09-28
For those interested, I fixed the problem by moving the card to the other PCI slot. Now the card is detected automatically and everything just works.

---

