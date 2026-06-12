---
title: "dhcpd conf question"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by tessio on 2011-04-15
Hello,
I'm trying to configure my dhcp3 server to give ip leases based on which interface the request came from..

Something like:
```

shared-network real-virtual {
 subnet 10.1.1.0 netmask 255.255.255.0 {
   option routers 10.1.1.1;
 }
 subnet 192.168.56.0 netmask 255.255.255.0 {
   option routers 192.168.56.1;
 }
 pool {
  #allow if from eth0
   range 10.1.1.100 10.1.1.250;
 }
 pool {
   #allow if from eth1
   range 192.168.56.100 192.168.56.250;
 }
}

```Is this even possible?

---

