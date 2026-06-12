---
title: "Interfaces file format."
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by andylockran86 on 2009-02-24
At the moment I run the following commands to set up a tun0 interface.

ip tunnel add tun0 mode ipip remote 192.168.1.11 local 192.168.1.14 dev eth2_rename
ifconfig tun0 10.50.0.1 netmask 255.255.255.252 pointopoint 10.50.0.2
ifconfig tun0 mtu 1500 up

How can I configure this in an /etc/network/interfaces file ?  Please let me know a resource I can query, or else provide the direct answer.

Regards,

Andy

---

### Post by Iowan on 2009-02-24
See if anything in [here]("https://help.ubuntu.com/community/SSH_VPN#Configuring%20the%20interfaces") is helpful.

---

