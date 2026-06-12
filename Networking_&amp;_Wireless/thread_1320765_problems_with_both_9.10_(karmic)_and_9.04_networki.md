---
title: "problems with both 9.10 (karmic) and 9.04 networking"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by deanec65 on 2009-11-09
just did a fresh install of both 9.10 and 9.04 X64 and I'm having major issues with A) being able to get updates and B) being able to browse the web. both releases are unable to connect to any website or forum that I can find! it sits at "waiting for {server name}" but pings work and I'm able to do FTP through the browser! please help since this is bugging the me NO end.

---

### Post by deanec65 on 2009-11-09
output of "sudo lshw -C network > network.txt

also at this exact time I'm running ubuntu 9.04 jaunty X64 bit! PLEASE HELP !
  *-network
       description: Ethernet interface
       product: 190 Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 00
       serial: 00:17:31:84:e8:8e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.1.2 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ce:21:5c:d9:95:2b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by deanec65 on 2009-11-09
also it can easily connect locally just no websites at all!

---

### Post by deanec65 on 2009-11-09
no help?

---

### Post by Iowan on 2009-11-09
Sometimes it more than an hour (or three) for some of us to get home from work and fire up the forum.
Post results of **route**. The last line should list your gateway. Another place to check is */etc/resolv.conf* to see if the proper nameservers are in place. DHCP or static addressing?

---

