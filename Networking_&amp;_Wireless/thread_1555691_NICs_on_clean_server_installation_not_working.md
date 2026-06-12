---
title: "NICs on clean server installation not working"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by Karl1982 on 2010-08-18
I have a clean installation of Ubuntu Server 10.04 x64 on an HP Proliant  DL380 G3.  It has two Broadcom NICs in addition to its ILO.  During the  installation, both NICs were listed... but neither was able to pull  DHCP, nor did they function with manual settings.  The first NIC is  currently connected and is known good.

So I left it alone and figured I'd troubleshoot it later (which is now).   This server is going to be a VMware Server host.  I wanted to install  ESXi on it, but it doesn't like the old server's cheap ICH RAID  controller.

Anyway, here are the output of ifconfig and the contents of /etc/network/interfaces:
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1776 (1.7 KB)  TX bytes:1776 (1.7 KB)
``````
auto lo
iface lo inet loopback
```They list only the loopback adapter.  Here are relevant lines from lspci:

```
01:02.0 System peripheral: Compaq Computer Corporation Integrated Lights Out Controller (rev 01)
01:02.2 System peripheral: Compaq Computer Corporation Integrated Lights Out  Processor (rev 01)
06:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 10)
06:01.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5704  Gigabit Ethernet (rev 10)
```So the hardware is seen by the system.   Here is lshw -class network:

```
  *-network:0 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5704 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:14:38:50:ef:7d
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.102 duplex=half firmware=5704-v3.27b, ASFIPMIc v2.36  latency=64 link=yes mingnt=64 multicast=yes port=twisted pair
       resources: irq:24 memory:fdef0000-fdefffff
  *-network:1 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5704 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1.1
       bus info: pci@0000:06:01.1
       logical name: eth1
       version: 10
       serial: 00:14:38:50:ef:7c
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.102 duplex=half firmware=5704-v3.27b latency=64 link=yes  mingnt=64 multicast=yes port=twisted pair
       resources: irq:25 memory:fdee0000-fdeeffff
```

I  noticed here it says they're disabled... so I thought perhaps this was a  64-bit driver issue.  So, I booted my trusty Ubuntu desktop 10.04  32-bit live cd, and the NIC works fine.  Now, here's where it gets  weird.  Seeing that, I booted it to Ubuntu server 10.04 32-bit  installation from a flash drive, expecting to see the NICs working fine  during the installation... but they have the same problem.  So what can I  do to resolve this?

---

### Post by Iowan on 2010-08-18
Have you tried configuring them in */etc/network/interfaces*?

---

### Post by Karl1982 on 2010-08-19
I have not... however, on my fully-functional Ubuntu laptop, my own */etc/network/interfaces* also only lists the loopback, and both wired eth0 and wireless eth1 work fine here.

I may have spoken too soon about the LiveCD.  I haven't tried it again to verify, but here's some new info.  I decided since my coworkers aren't as familiar with Ubuntu as I am (I work in a shop with a dozen or so Windows servers), I installed Xubuntu alternate x64 on the server to give it a functional GUI.  Now, while */etc/network/interfaces* still only defines the loopback adapter, eth0 does come up and successfully query DHCP.  I can run *dhclient* and see that the process works again.  But then I can't pass any traffic back to the server that just issued me DHCPACK.  And in the notification area, I can look at the connection info, and it all looks good...

The server can't ping out or respond to pings.  Although it does appear to be functioning as far as DHCP, it's not responding to ARP requests either (checked with wireshark).

---

