---
title: "Wired networking instability"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by J0ris on 2011-03-22
Hi,

I'm having trouble keeping a stable connection to my local network. All external factors have been ruled out (cable, router, hub).
Symptoms: Network goes down after soft reboot and ONLY comes on again when restarting after shutdown AND turning off electricity.
Networking stays functional when logging out and logging back in, however.
Looked around in the log files a bit but nothing apparent.
Hardware is the following:

Ethernet interface
product: 82566MM Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 03
serial: 00:01:80:67:7e:c1
size: 100MB/s
capacity: 1GB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=0.3-0 ip=192.168.0.193 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
resources: irq:40 memory:fdfc0000-fdfdffff memory:fdfff000-fdffffff ioport:fe00(size=32)

Machine is a 3-year-old Aopen MP965-DR

Any suggestions?

Thanks

---

### Post by SecretLegend on 2011-03-22
I have had this problem with other NIC's but never dug into it too deeply I mostly just replaced the NIC's with PCI ones that were gigabit ethernet hope some one can help you man :D

---

