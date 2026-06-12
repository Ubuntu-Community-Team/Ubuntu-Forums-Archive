---
title: "Unable to enable wireless adapter."
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by brainard52 on 2011-05-01
I just got a HP Pavilion dv6, and I am unable to ENable the wireless adapter. what can I do to get you the information that you need to help me out?

I have a broadcom Adapter. i am running updates to see if that helps any, and I will get back to you on that. I ran ```
lshw -C network
``` and it gave me:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:d9500000-d9503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:5a:fb:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.6 latency=0 multicast=yes
       resources: irq:29 ioport:5000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)

```Hope that helps some.

By the way, i have a feeling that it has something to with this little bugger... the orange touch button. [IMG]http://img607.imageshack.us/img607/534/sam0302.th.jpg[/IMG]

---

### Post by brainard52 on 2011-05-01
solved with an update... aparently there was a proprietary that I needed that wasn't recognised by the version of Ubuntu I had. half hour long update. psh...

---

