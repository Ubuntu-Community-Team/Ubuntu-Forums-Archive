---
title: "replaced mobo - no network"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by realjaja on 2010-05-05
[FIXED]!!!  upgraded to 9.10 and my problems are gone...
(how I upgraded was fun.... I didn't have a CD/DVD drive so I put the drive in my backup shuttle pc.... network worked fine there, so I did the apt-get upgrade thingy and went from 8.10 -> 9.04 -> 9.10 [didn't check if 9.04 would've worked....])



(UBUNTU 8.10)

i reinstalled a different motherboard and having network problems.

new one is a G31TM-P21, 

sudo lshw -C network shows:
RTL8101E/8102E

was puzzles me is that I have another system running 8.04 flawlessly on the same motherboard.

difference is 

8.04   r8169 v2.2LK
8.10   r8169 v2.3LK-NAPI


1. deleted the new entries on the 70-persistent.net.... file so that eth0 was revised.

2. for some reason ifconfig show billions of dropped packets

3. i read about the r816x drivers being buggy, and found some fixes, hesitant to do anything simply because it is working on the 8.04 with v2.2.

4. tried the blacklist trick for ipv6

any ideas?

(and i know the system works because i install it in to a shuttle cube and networking works flawlessly.)

i probably didn't include nearly enough details....

---

### Post by realjaja on 2010-05-05
not sure what the bump rule is on this forum.... sorry if i broke any rules...

so put the system in my backup shuttle system, and its working perfectly.


$ ethtool -i eth0
driver: tg3
version: 3.94
firmware-version: 5751-v3.24a
bus-info: 0000:01:00.0

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751-v3.24a ip= latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=1GB/s




but since this is a REAL temporary system, i'd like to get it back in my rack system with the new mobo.... help?

---

### Post by eltonw on 2010-05-05
> **realjaja said:**
> not sure what the bump rule is on this forum.... sorry if i broke any rules...

so put the system in my backup shuttle system, and its working perfectly.


$ ethtool -i eth0
driver: tg3
version: 3.94
firmware-version: 5751-v3.24a
bus-info: 0000:01:00.0

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751-v3.24a ip= latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=1GB/s




but since this is a REAL temporary system, i'd like to get it back in my rack system with the new mobo.... help?

Your original post indicates a RaLink network card. Kindly see my post here:
[http://ubuntuforums.org/showthread.php?t=1473629]("http://ubuntuforums.org/showthread.php?t=1473629")

HTH...

---

### Post by realjaja on 2010-05-05
elton,

thx for the links, but didn't occur to me that a simple upgrade could solve all my problems... i was so caught up in the 8.04 works and 8.10 not working thing...

anyway i upgraded all the way up to 9.10 (did 8.10 -> 9.04 -> 9.10) and ALL is good.

(was 10 min away from ordering another mobo :)  )

---

### Post by Iowan on 2010-05-05
If it *remains* fixed, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :D

---

