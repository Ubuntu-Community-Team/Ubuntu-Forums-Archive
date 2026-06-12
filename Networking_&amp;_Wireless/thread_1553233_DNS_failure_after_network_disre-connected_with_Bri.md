---
title: "DNS failure after network dis/re-connected with Bridged Inet"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by ub-newbie on 2010-08-14
Posting this so I can find the fix, and it might effect others.

Using 10.4, with ETHO & ETH1 bridged to BR0 with bridge_utils.

Symptoms:  When Cat-5 is disconnected, then reconnected Ubuntu will not resolve DNS or access Internet until I reboot.  Problem is reproducible & is not seen on Windoz.

```
ifconfig
``` shows the same IP on 
ETH0 
```
eth0      Link encap:Ethernet  HWaddr 00:0c:76:2b:97:97  
          inet addr:192.168.8.22  Bcast:192.168.255.255  Mask:255.255.0.
```
and BR0:
```
br0       Link encap:Ethernet  HWaddr 00:0c:76:2b:97:97  
          inet addr:192.168.8.22  Bcast:192.168.4.255  Mask:255.255.255.0
```

Solution:  ```
ifconfig -v eth0 0.0.0.0
``` (might require sudo?)

Symptoms after fix:
    While dis/re-connecting CAT-5 still causes loss of DNS, 'IFDOWN BR0', 'IFUP BRO' and above "solution" gets me back online without a reboot.

Theory:
  As stated in the Bridge_Utils readme... "eth0 and eth1 should not have IP addresses allocated to them"

---

