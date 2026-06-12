---
title: "[HELP]Destination Host Unreachable On Multiple eth and Multiple Gateway"
date: 2010-05-26
forum: Networking &amp; Wireless
---

### Post by sangprabv on 2010-05-26
I'm doing some connectivity test with 3 ethernet cards. The configuration is:

eth0 202.153.193.193/27
eth1 192.168.8.1/24
eth2 192.168.31.116/29

202.153.193.222 (eth0) is the default gateway
192.168.8.1 (eth1) has no gateway since it acts as gateway
192.168.31.113 (eth2) should be the gateway for 192.168.31.116

The question is how to add 192.168.31.113 into the routing table and make it ping able. I tried to do with
route add -net 192.168.31.112 netmask 255.255.255.248 gw 192.168.31.113 and still fails to ping it. But if I try with a pc which only has a single ethernet card and assign it manually 192.168.31.116/29 and set the gateway to 192.168.31.113 it works smoothly. Many thanks for any response.

---

