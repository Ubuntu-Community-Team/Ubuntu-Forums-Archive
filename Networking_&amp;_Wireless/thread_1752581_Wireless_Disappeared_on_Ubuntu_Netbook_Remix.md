---
title: "Wireless Disappeared on Ubuntu Netbook Remix"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by olamina on 2011-05-08
After installing Ubuntu Netbook Remix on my Toshiba NB505, I hoped the wireless would just work right away, but it didn't. After much searching, I [found these instructions (scroll down to High Horse's response at #3)]("https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667"), which directed me to download the Realtek Driver RTL8192SE. I followed the directions to a T and everything was working wonderfully, until a recent restart that has taken me back to square one. I think the default Ubuntu drivers may be overriding the drivers I installed and putting everything back to default (no wireless), but I'm not sure. Here's the latest output:

```
olamina@ubuntu:~$ sudo su  
 root@ubuntu:/home/olamina# lshw -C Network  
   *-network UNCLAIMED      
        description: Network controller  
        product: Realtek Semiconductor Co., Ltd.  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:07:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list  
        configuration: latency=0  
        resources: ioport:2000(size=256) memory:f0100000-f0103fff  
   *-network  
        description: Ethernet interface  
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller  
        vendor: 

Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:09:00.0  
        logical name: eth0  
        version: 05  
        serial: 1c:75:08:77:01:1e  
        size: 10MB/s  
        capacity: 100MB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s  
        resources: irq:43 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff  

```Any help in terms of fixing the problem and preventing it from reverting again is appreciated BIG TIME. I want to get to a point where I can finally stop duel booting.

---

### Post by olamina on 2011-05-25
UPDATE: I upgraded to 11.04 Natty Narwhal and the problem fixed itself. Not sure if this counts as SOLVED. I guess so.

---

