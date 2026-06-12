---
title: "wireless keeps disconnecting *Information included*"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by TravisFo on 2010-11-04
My wireless connection keeps dropping is very unstable, signal strength goes up and down here is the info i got from the terminal


 *-network:0             
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:e8:e9:d0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:11 memory:c2004000-c2004fff ioport:3000(size=64)
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:08:9a:a4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.103 latency=64 maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:11 memory:c2005000-c2005fff

---

### Post by wieman01 on 2010-11-04
This could also be due to kernel problem, I saw related posts. A kernel upgrade to 2.6.36 could help solve the problem.

---

### Post by P4man on 2010-11-04
Are you sure its an ubuntu issue? I mean does the same card work better in windows? Its a rather .. mature (read: old) card which ought to be well supported. But that wont help if you have interference on your AP. Have you tried another channel?

---

### Post by Chrisco66 on 2010-12-14
Mine is doing the same thing in 10.04.  Same hardware.  Worked well in windows, and with 9.10.  Any ideas?

---

