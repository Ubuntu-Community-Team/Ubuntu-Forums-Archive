---
title: "EW-7608Pg pci on Ubuntu 11.10 - no wireless connection."
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by ksht on 2012-02-11
A freshly installed Ubuntu 11.10 on my desktop - everything seems to work just fine except the wireless Internet connection. Unfortunately, I can't connect a usual wired cable due to the remote computer location. I have Edimax PCI EW-7608Pg wireless card on my computer. I am relatively new to -nixes but it seems the problem is the system just doesn't recognize the card.
After executing this terminal command [sudo lshw -C network] I obtained the following:
kshtwohn@kshtwohn-desktop:~$ sudo lshw -C network 
[sudo] password for kshtwohn: 
  *-network               
       description: Ethernet interface 
       product: RTL-8169 Gigabit Ethernet 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 9 
       bus info: pci@0000:02:09.0 
       logical name: eth0 
       version: 10 
       serial: 00:14:85:e2:12:26 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s 
       resources: irq:20 ioport:a400(size=256) memory:fc000000-fc0000ff memory:50000000-5000ffff 
kshtwohn@kshtwohn-desktop:~$ 

so as far as I can see the system was able to recognize my Ethernet port only. Then I went to the website of Edimax just to find out that they suggest a Linux driver for my card with .tar.gz extension. I have no idea now what should I do - I don't even know how to install this .tar.gz driver, if needed. Please, help.

---

### Post by praseodym on 2012-02-11
Hi,

please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
iwconfig
```

---

