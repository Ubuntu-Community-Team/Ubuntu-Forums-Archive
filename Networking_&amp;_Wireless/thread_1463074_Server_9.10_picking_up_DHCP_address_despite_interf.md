---
title: "Server 9.10 picking up DHCP address despite interfaces configured for static IPs."
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by mathlaura on 2010-04-26
I've installed 7 Ubunto 9.10 servers.  I initially configured them for DHCP address assignment, and subsequently edited /etc/network/interfaces with static IPs, edited resolv.conf with static DNS server addresses, and restarted networking services.  After about 12 hours, every one of the servers IP addresses changed to a DHCP address again.  I then removed dhcp-client and restarted networking again.  The servers changed to their assigned static IPs again.  Then, over the weekend, they again picked up DHCP addresses.  Restarting networking fixes it every time, but I can't figure out how they're getting dynamically-assigned addresses at all.  Ideas?  

For reference, here is one of the interfaces file, with IPs changed:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.10.10.243
netmask 255.255.255.0
network 10.10.10.0
broadcast 10.10.10.255
gateway 10.10.10.1

---

### Post by mathlaura on 2010-04-26
Purging dhcp3 seems to fix this, but I'm unclear on why that is necessary.

---

### Post by Iowan on 2010-04-26
Although it shouldn't, the "leases" file (or something using it) might have triggered the machine to "renew" it's IP address. */var/lib/dhcp3/dhclient.eth0.leases * is where my machines keeps it's address.

---

