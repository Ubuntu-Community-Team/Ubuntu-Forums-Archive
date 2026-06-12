---
title: "Link Aggregation guides up-to-date for 11.10?"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by prupert on 2012-03-01
Hi All

I have a server with two NICs and one WLAN. I would like to use LinkAggregation, but I wanted to check that the instructions here:

[https://help.ubuntu.com/community/LinkAggregation](https://help.ubuntu.com/community/LinkAggregation)

and here:

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

are accurate and relevant to Ubuntu (Lubuntu 11.10? Obviously there is some specific stuff to 10.04 and above and I shall follow that, but I wanted to ensure there isn't anything missing there.

I am planning to use bond mode 0.

The two NICs and the WLAN will be connected on the same LAN, which is my home LAN. I would like to use Link Aggregation because the two NICs are connected to two Powerline Adaptors, which seem somewhat flakey (the server is sadly too far away to use cable and the wife wont let me drill a hole through the wall :(). The idea is to use all three inerfaces to basically act as failover support.

---

### Post by prupert on 2012-03-02
So, to answer my own question, NO neither of those pages work. I have managed to get the following configuration to work:

```
auto eth0
iface eth0 inet manual
 bond-master bond0

#adapter bonding
auto bond0

iface bond0 inet static
address 192.168.1.70
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1
post-up ifenslave bond0 eth0 eth1
pre-down ifensalve -d bond0 eth0 eth1
#bond-slaves eth0 eth1
bond_mode 0
bond_miimon 100
```

BUT, eth1 only connects at 10MB/S when it should be 1000MB/S.

Any one:
- care to comment on the configuration above
- know why eth1 only connects at 10MB/S?

Cheers

---

