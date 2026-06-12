---
title: "2 networks and ARP"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by newton_9 on 2010-12-06
Hello

I am new to ubuntu and have two ethernets devices on my laptop. i would like to attach 1 printer on eth1. my network settings are

eth0 is DHCP.. and its working fine

eth1 has..
ifconfig eth1 10.10.0.10 netmask 255.255.255.0

I am removing network printer from the network and attaching with eth1. The printer default settings are:

IP= 192.168.16.43
netmask= 255.255.0.0
gwe= 192.168.0.1

After attaching this printer if i try to send 'arp -a -i eth1' command to get printer IP & MAc address. it returns with empty data. What i understood is 'arp' doesn't work on different subnets or networks?

All i want is to extract printer network settings through some commands. can anyone guide me towards correct direction ??

anxiously waiting

regards

---

### Post by newton_9 on 2010-12-07
any 1???

---

