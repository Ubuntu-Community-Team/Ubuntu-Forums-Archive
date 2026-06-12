---
title: "Dell 2800 server w/multiple nic's"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by quikone8 on 2009-10-28
For some reason I cannot get both cards to activate at the same time.  I would like to have one card for lan (dynamic) and one for wan (static).  Does anyone know how to solve this?  BTW the cards are; Intel Corporation 82541GI Gigabit Ethernet Controllers.

---

### Post by Iowan on 2009-10-28
How/where are the cards configured.  For both to be active, (at least) one will (probably) need to be defined in */etc/network/interfaces*.
(Although I just discovered my laptop connecting via wired and wireless simultaneously... managed by NM ???)

---

### Post by quikone8 on 2009-10-28
> **Iowan said:**
> How/where are the cards configured.  For both to be active, (at least) one will (probably) need to be defined in */etc/network/interfaces*.
(Although I just discovered my laptop connecting via wired and wireless simultaneously... managed by NM ???)

They are configured in /etc/network/interfaces.  Not managed by NM, it was too much trouble.  It is managed manually.  I have noticed though that when one is up the other is down and vice versa.

---

### Post by Iowan on 2009-10-28
Post your */etc/network/interfaces*. Having them both in the same subnet can cause problems.

---

### Post by quikone8 on 2009-10-28
> **Iowan said:**
> Post your */etc/network/interfaces*. Having them both in the same subnet can cause problems.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# he loopback network interface
auto loT
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.1.251
netmask 255.255.255.0
gateway 192.168.1.1

iface eth1 inet static
address 192.168.1.252
netmask 255.255.255.0
gateway 192.168.1.1





auto eth1

---

### Post by Iowan on 2009-10-29
Well, they are both in the same subnet. (eth0 has no "auto" line). Which one did you intend to have the dynamic address (both are configured for static). Is suspect the WAN address would get the dynamic address, and the LAN address would be static... but which is which?

---

### Post by ant2ne on 2009-10-29
how do you know one is up and one is down? Are you doing an ifconfig? Could this be a bios setting?

---

### Post by quikone8 on 2009-10-29
> **Iowan said:**
> Well, they are both in the same subnet. (eth0 has no "auto" line). Which one did you intend to have the dynamic address (both are configured for static). Is suspect the WAN address would get the dynamic address, and the LAN address would be static... but which is which?

You are right!  The problem is I cannot keep both nic's active.

---

### Post by Iowan on 2009-10-29
Try setting them up in different subnets - just to see if they both stay active.

---

