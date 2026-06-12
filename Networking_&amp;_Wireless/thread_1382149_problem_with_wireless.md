---
title: "problem with wireless"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by moufasa on 2010-01-15
Hi, i have recently purchase the Toshiba Laptop Satellite L500-1D9 with wifi card rtl8191se and i have installed ubuntu 9.04 jaunty.
i tried to follow the directions from here [https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper) with not result any suggestions?
Thank you in advance..

---

### Post by bkratz on 2010-01-15
> **moufasa said:**
> Hi, i have recently purchase the Toshiba Laptop Satellite L500-1D9 with wifi card rtl8191se and i have installed ubuntu 9.04 jaunty.
i tried to follow the directions from here [https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper) with not result any suggestions?
Thank you in advance..

Do you see the network icon at the top of the screen. What state is it in. What is the problem.

---

### Post by moufasa on 2010-01-15
rigth now i am online in a wired network wicd manager can not find any wireless network

---

### Post by bkratz on 2010-01-15
> **moufasa said:**
> rigth now i am online in a wired network wicd manager can not find any wireless network

Usually with network manager and I suspect WICD is the same (but don't know for sure) you have to disconnect the wired to use the wireless.

---

### Post by moufasa on 2010-01-15
it does not help..in wicd manager in preferences near wireless device it does not hace any device is that ok?

---

### Post by bkratz on 2010-01-15
> **moufasa said:**
> it does not help..in wicd manager in preferences near wireless device it does not hace any device is that ok?

Well if we drop to the terminal (Applications>>Accessories>>Terminal) and type in
sudo iwlist scan 
it should show whatever networks are close by along with type of encryption
If you don't see anything post the output of 
sudo lshw -C network

(that is a LSHW in lowercase)
back here (copy/paste)

---

### Post by moufasa on 2010-01-15
the output of the first command is
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

and of the second


*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:f0:7d:e4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.254.1 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: f2:22:cd:26:3a:91
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by moufasa on 2010-01-15
what can i do now?is there an other guide to follow?an other distribution of linux that will not have the same problem?

---

### Post by khairdean on 2010-01-16
hi there i have a similar problem, but when i do "sudo iwlist scan" i get

wlan0     Failed to read scan data : Operation not permitted


please help!!!!

---

### Post by bkratz on 2010-01-16
@moufasa

It doesn't seem to tell what the wireless card is here. How about trying

lspci | grep Wireless 
or if no result
lspci -nn
(those are both LSPCI in lowercase)

@khairdean
Don't know what that is--could it have been spelling or it did ask for your password didn't it?

---

### Post by khairdean on 2010-01-16
yes this is the whole thing:


[sudo] password for khairdean: 
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Failed to read scan data : Operation not permitted

eth0      Interface doesn't support scanning.

---

