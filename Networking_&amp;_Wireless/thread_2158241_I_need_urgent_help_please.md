---
title: "I need urgent help please"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by plopes on 2013-06-28
I have 2 machines (A and B) both have 2 NICs (PCI nic and external nic). I'm trying to directly connect them via static route. I have configured both interfaces (gedit /etc/network/interfaces) with correct IPs, e.g IP: 10.1.1.1 Netmask 255.255.255.0 Network 10.1.1.0 Gateway 10.1.1.2 (machine B IP address).

If i direct connect both PCI NICs it works good and i can ping in both directions.
 
          A                  B
 eth0 |   | -------- |   | eth0 (works) PCI NICs

But if i direct connect NOT PCI NICs and do all the changes in the interfaces file like chanching the interface name to eth1, it not works.

 eth1 |   | -------- |   | eth1 (NOT works)

And if i direct connect both eth1 interfaces to ethernet interface in my laptop it works. 

What im doing wrong?

---

### Post by Kujua on 2013-06-30
> But if i direct connect NOT PCI NICs and do all the changes in the interfaces file like chanching the interface name to eth1, it not works.
Instead of changing interface name from eth0 to eth1, add new set of configuration for eth1. Perhaps old ARP entries from eth0 link is causing the problem.
eg: eth0 A: 10.1.1.1
      eth0 B: 10.1.1.2

      eth1 A: 10.1.2.1
      eth1 B: 10.1.2.2

I am not sure this is the problem, just guessing (since no one else replied).

---

