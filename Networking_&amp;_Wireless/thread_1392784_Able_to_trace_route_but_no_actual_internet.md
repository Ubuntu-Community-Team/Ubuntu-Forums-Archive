---
title: "Able to trace route but no actual internet"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Pindaman on 2010-01-28
Hello,

I use VMware Workstation with Ubuntu Server. But after having searched for this for more then 10 hours i figured its time to make a topic.

My problem is that i can ping [www.anything.com]("http://www.anything.com") and also use "host" and "trace route" on everything. But as soon as i try to wget or apt-get update or install, nothing happens.

Things i have tried so far:
- Use VMware Server instead of Workstation
- Ubuntu Desktop instead of Server version
- Configure OpenDNS as the DNS etc.
- Bridged instead of my preferred NAT
- Firewall off on host OS
- Disabled IPV6 in Grub bootloader
- Static and DHCP ip addresses

I tried the NAT static way like this (preferred):
/etc/network/interfaces
auto eth1
iface eth1 inet static
address 192.168.205.90
gateway 192.168.205.2
netmask 255.255.255.0
network 192.168.205.0
broadcast 192.168.205.255

The bridged method with these settings:
auto eth1
iface eth1 inet static
address 192.168.1.111
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

Both with these DNS settings:
/etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.220.220

But all of the above didnt work out for me. I hope someone knows a solution to my problem. I can also ping to the apt-get resources its trying to update from.

Nigel

---

### Post by Pindaman on 2010-01-28
Ok so i got it working via Bridged. By just using DHCP. But that isnt what i _really_ want since its a test SVN server but ill stick with this i guess.

Ill close the topic. Thnx for reading.

Edit: Cant find how to close it.

---

### Post by Iowan on 2010-01-28
How to mark it [[SOLVED]]("http://https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

