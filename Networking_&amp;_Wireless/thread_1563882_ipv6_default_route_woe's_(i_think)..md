---
title: "ipv6 default route woe's (i think)."
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by Shihan74 on 2010-08-29
Hi Guys,

hoping someone might able to clear something up for me.

I've got an ipv6/ipv4 dual-stack network which is now uplinked into the real world and i'm having drama's with the routing of data.

it seems something is getting a little messed up with the routing of packets cause when i login i have two default routes, one just routes out thru eth0, the other goes to the link-local of the router. If i remove the default route thru eth0, everything works, but im not sure where or why linux is putting in that default route in the first place? any suggestions?

TIA

---

### Post by Stolen on 2010-08-30
How are you getting your IPv6 address?  Static, dhcpv6, or SLAAC?
If SLAAC, you might want to install ndisc6 (sudo apt-get install ndisc6) and run "rdisc6 <interface>" to see what routes are being advertised to you.

```
# rdisc6 eth2
Soliciting ff02::2 (ff02::2) on eth2...

Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :           No
Router preference         :         high
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
 Prefix                   : 2001:470:81e5::/64
  Valid time              :        86400 (0x00015180) seconds
  Pref. time              :        14400 (0x00003840) seconds
 Recursive DNS server     : 2001:470:81e5::1
  DNS server lifetime     :          600 (0x00000258) seconds
 Source link-layer address: 00:22:3F:F6:2C:33
 from fe80::222:3fff:fef6:2c33

```
here, my router is fe80::222:3fff:fef6:2c33.  If there was more than one router responding to router discoveries, you'd have similar info displayed for each one.

Also, to help us out, you might want to give us the output of "route -6" so we can see exactly what's showing up in your routing table.

---

### Post by Shihan74 on 2010-09-01
All the linux boxes on my network appear to do pretty much the same thing... when i do the rdisc, i get this:

```

$ rdisc6 eth0
Soliciting ff02::2 (ff02::2) on eth0...

Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :           No
Router preference         :         high
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
 MTU                      :         1500 bytes (valid)
 Prefix                   : 2001:470:1f05:1085::/64
  Valid time              :      2592000 (0x00278d00) seconds
  Pref. time              :       604800 (0x00093a80) seconds
 Prefix                   : ::/0
  Valid time              :      2592000 (0x00278d00) seconds
  Pref. time              :       604800 (0x00093a80) seconds
 from fe80::210:dbff:fe91:9a20

```

however, this is the route table on the problem machine after its booted:
```

# route -6
Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2001:470:1f05:1085::/64        ::                         UAe  256 0     2 eth0
fe80::/64                      ::                         U    256 0     0 eth0
::/0                           ::                         UAe  256 0     2 eth0
::/0                           fe80::210:dbff:fe91:9a20   UGDAe 1024 0     2 eth0
::/0                           ::                         !n   -1  1    45 lo
::1/128                        ::                         Un   0   3   317 lo
2001:470:1f05:1085:219:b9ff:fe6d:7f1e/128 ::                         Un   0   1    60 lo
fe80::219:b9ff:fe6d:7f1e/128   ::                         Un   0   1     0 lo
ff00::/8                       ::                         U    256 0     0 eth0
::/0                           ::                         !n   -1  1    45 lo

```


alot of the linux machines display the "non-functional" version of the routes which in reality is only this particular line (or at least, remove it and im good):

```

::/0                           ::                         UAe  256 0     2 eth0

```

---

