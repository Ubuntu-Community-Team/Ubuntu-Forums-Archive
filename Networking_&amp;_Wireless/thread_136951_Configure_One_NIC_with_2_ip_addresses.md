---
title: "Configure One NIC with 2 ip addresses"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by _hadi_ on 2006-02-27
Dear All,
I want to access to 2 local networks with just one nic.
How can I configure my nic with 2 ip addresses.
I know that it is possible in fedora to do that.
Is it possible in ubuntu? :confused:

---

### Post by _hadi_ on 2006-02-27
Dear All,
Yeeeees. It is possible.

Just add your configs to /etc/network/interfaces with another name.
Think your 1st ip config is:

iface eth0 inet static
address 172.xxx.xxx.xxx
netmask 255.255.xxx.xxx
...
auto eth0

Now for another ip :

iface eth0:1 inet static
address 192.xxx.xxx.xxx
netmask 255.255.xxx.xxx
auto eth0:1

You can redo it for other ips as well.

---

