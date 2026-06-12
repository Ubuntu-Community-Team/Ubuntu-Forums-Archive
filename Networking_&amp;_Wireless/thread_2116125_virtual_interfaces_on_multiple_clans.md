---
title: "virtual interfaces on multiple clans"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by marsred on 2013-02-14
Hi there,

I have an Ubuntu Server 12.04 machine with one physical NIC connected to a trunk port on a Cisco switch. I've installed the vlan package and configured /etc/network/interfaces to use 5 virtual interfaces with static IPs with vlan tagging, each on a different vlan.

The problem I've run into is that only one of the virtual interfaces seems to be "active" at a time, meaning only one of the IP addresses can be pinged. Sometimes, with a restart, which interface this works on will change. I had read that I should only configure the gateway on one of the interfaces, so I did, but that's not even the interface that always works!

Any ideas?

Thanks.

---

