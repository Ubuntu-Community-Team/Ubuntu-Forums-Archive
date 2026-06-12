---
title: "Some help with IP MAsquerading."
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by Davion on 2009-06-02
Hi guys,
I have a problem with ip masquerade.
I have two pcs, one Master node and one Slave Node. Master node is running Ubuntu 9.04 x64 and the slave node is running Ubuntu Server x64.
Master node has 3 nics..
eth0 for NFS 
eth2 for internet connection 
eth1 for other purposes.

Slave node has 2 nics
eth0 for nfs/pxe boot
eth4
and loads it's OS via PXE boot from Master node through nfs over eth0.

At master node i setted up a dhcp server in order to assign an ip address to slave's eth0 nic.
So master and slave node communicate via nfs over eth0 nics.

Master node access internet over eth2 which is connected to a router.

The ip addresses are...

Master node
eth0: 192.168.2.1 static
eth2: 192.168.1.66 router's dhcp
eth1: not in use yet

Slave node
eth0: 192.168.2.2 via master's dhcp server
eth4: not assigned

So..I want to make slave node to "see" internet over it's eth0 nic. I try different ways but the problem remains..

Any help would be appresiated..Thanks in advance!

---

### Post by Davion on 2009-06-02
Any suggestions??

---

### Post by Iowan on 2009-06-02
Seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ICS help page?

---

### Post by Davion on 2009-06-03
I didn't see that page to be honest but i tried some of these things..
Finally i did it by installing Firestarter..It is very easy to share the internet connection using Firestarter (2 or 3 clicks!) something that i didn't know until i used it. Everything is working fine now and both nodes have internet. Anyway thanks for your reply!

---

### Post by Iowan on 2009-06-03
I haven't used Firestarter or UFW... but it's on my to-do list.

---

