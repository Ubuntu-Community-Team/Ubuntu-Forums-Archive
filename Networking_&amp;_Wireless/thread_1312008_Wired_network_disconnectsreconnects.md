---
title: "Wired network disconnects/reconnects"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by kevin.krenz on 2009-11-02
Hi all,

I'm having a strange issue where NetworkManager goes in a loop of trying to connect to a wired usb connection, then disconnects, and then tries to connect, etc. The strange part is that I'm not using any usb devices; I'm just connected to my wireless network.

I've attached the relevant output in the syslog for one loop, but haven't been able to make much of it. Any ideas?

Thanks!

Kevin

---

### Post by Iowan on 2009-11-03
Anything interesting from **lshw -C network**?

---

### Post by kevin.krenz on 2009-11-04
Here's the output of **lshw -C network**. usb0 disappears and reappears as NetworkManger disconnects and reconnects. I've also learned today that suspending the computer and then waking it up makes the issue go away, which is a reasonable workaround for now.

```
 *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:98:07:ab
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:fc000000-fc01ffff memory:fc025000-fc025fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:c2:e1:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=10.102.3.6 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f4300000-f4301fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=no multicast=yes

```

---

### Post by Iowan on 2009-11-04
You can see if usb0 shows up in  */udev/rules.d/70-persistent-net.rules*

---

### Post by Fuddi on 2009-12-28
I have the same problem - did you find any permanent solution? 

Thanks.

---

