---
title: "Wireless manager stops working - was always fine before"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by rrsodl on 2011-06-05
I have a Samsung NC10 Plus which I understand it's just a N150

Running Ubuntu 10.10 Kernel 2.6.35-28

On installation I installed "Modaliases for the Broadcom 802.11 Linux STA driver"

I've never had this problem before but happened yesterday and I thought nothing of it. Last night it happened again..... this morning I was actually looking at the time when I saw the network manager icon disappear before my eyes :-)

I get it back by logging out and back in again.

I don't really know much about Ubuntu to find the problem..... my guess is that I must have updated something that is having an effect on the wireless manager..... the problem is I don't know how to find out what was updated last.

I found this command 

```
sudo lshw -C network
*-network               
       description: Wireless interface
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:0b:6b:7c:62:52
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.21 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:f0100000-f0103fff
  


```
 
I need help to find out what is causing this problem / fix the problem
and I would like to know how to restart the wireless manager....
I tried 

```
sudo /etc/init.d/networking restart
```

no luck with that :-)

Thank you

---

### Post by rrsodl on 2011-06-17
What is the command line to search for available wireless networks?

Thanks

---

