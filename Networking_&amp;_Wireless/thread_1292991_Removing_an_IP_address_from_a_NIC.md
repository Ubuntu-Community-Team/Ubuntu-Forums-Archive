---
title: "Removing an IP address from a NIC"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by beavis69 on 2009-10-16
For some odd reason a machine that has one nic has two IP addresses assigned to it. There doesn't seem to be a reason for it, both IP's return the same services using nmap and both has the same URL.  I need to remove one of the IP addresses.

This is what it looks like using ip addr:

inet 1.2.3.10/29 brd 1.2.3.15 scope global eth0
inet 1.2.3.11/29 brd 1.2.3.15 scope global secondary eth0:1

If I wanted to remove eth0:1, how do I go about it? 

I tried editing vi /etc/network/interfaces and commented out these lines:

auto eth0:1
iface eth0:1 inet static
address 1.2.3.11
netmask 255.255.255.248

And ran sudo /etc/init.d/networking restart and eth0:1 still shows up in ip addr. THis is on Ubuntu 8.04.2

---

