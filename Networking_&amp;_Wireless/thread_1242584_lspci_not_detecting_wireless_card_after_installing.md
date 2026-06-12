---
title: "lspci not detecting wireless card after installing ubuntu"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by chiangs on 2009-08-17
Laptop came with Vista but I've just installed Ubuntu on it. Wireless was fine in Vista but does not work under ubuntu. My thinkpad uses "ThinkPad 11b/g III Wi-Fi wireless LAN Mini-PCIe" wireless card

however, it's not being detected lspci and Network Manager can only detect my ethernet. 


[root@chris ~]$ lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LF Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:7e:6b:07:fd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 ip=192.168.11.5 latency=0 multicast=yes
       resources: irq:29 memory:fc000000-fc01ffff memory:fc024000-fc024fff ioport:1820(size=32)
  ***-network UNCLAIMED** **( i think this is my wireless card?)**
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f4300000-f4303fff
[admin@chris ~]$ 

what driver can I install for me to re establish wireless networking?:confused:

thanks

---

### Post by chili555 on 2009-08-17
> *-network UNCLAIMED ( i think this is my wireless card?)Yes, indeed. What model of Thinkpad is it? We can, hopefully, track it down from the model.

---

### Post by gunterhausfrau on 2011-01-05
I'm having this same problem, though it was working a while back on Ubuntu, then I did an upgrade, from 8.10 to 9.10 (and traveled with it) and no more wireless. I couldn't downgrade so did a fresh install and tried several versions, no luck. I have since used it wired. It is a Thinkpad R51 2888-47u.

lspci doesn't show anything wireless, just the intel pro/100 which I believe is the wired adapter, yes?

Thanks.

---

