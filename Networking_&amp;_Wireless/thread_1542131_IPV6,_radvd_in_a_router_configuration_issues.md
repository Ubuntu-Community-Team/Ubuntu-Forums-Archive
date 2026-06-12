---
title: "IPV6, radvd in a router configuration issues"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by babazako on 2010-07-30
Hi all,

I am having some issues with radvd in a router configuration.
here is a scheme of my situation.
  ```

  _____                   __________
 |Client  |              |Router      |
 |eth0    |<-----------> |eth0<-->ppp0|<----->ISP
  --------                -----------

```I don't have any issues regarding my Client to Router, just ISP to router. The connection to the ISP works on other machines and also directly on the Client.

I think that it is a routing issue. I have tried to forward all my IPv6 traffic via ppp0 but no luck.

here is my routing table
```

Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2001:xxxx:xxxx:xxx::/64       ::                         UAe  256 0   111 eth0
fe80::/64                      ::                         U    256 0     0 ppp0
fe80::/64                      ::                         U    256 0     0 ath1.2
fe80::/64                      ::                         U    256 0     0 ath1.1
fe80::/64                      ::                         U    256 0     0 ath1.0
fe80::/64                      ::                         U    256 0     0 eth0
fe80::/10                      ::                         U    1   0     0 ppp0
fe80::/10                      ::                         U    256 0     0 ppp0
::/0                           ::                         U    1   0     0 ppp0
::/0                           ::                         !n   -1  1  3410 lo
::1/128                        ::                         Un   0   1     7 lo
2001:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx/128 ::                         Un   0   1     0 lo
2a01xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx/128 ::                         Un   0   1     0 lo
fe80::206:xxxx:xxxx:xxxx/128   ::                         Un   0   1     0 lo
fe80::206:xxxx:xxxx:xxxx/128   ::                         Un   0   1     0 lo
fe80::206:xxxx:xxxx:xxxx/128   ::                         Un   0   1     0 lo
fe80::260:xxxx:xxxx:xxxx/128   ::                         Un   0   1     0 lo
fe80::ffff:ffff:ffff:ffff/128  ::                         Un   0   1     0 lo
ff00::/8                       ::                         U    256 0     0 ppp0
ff00::/8                       ::                         U    256 0     0 ath1.2
ff00::/8                       ::                         U    256 0     0 ath1.1
ff00::/8                       ::                         U    256 0     0 ath1.0
ff00::/8                       ::                         U    256 0     0 eth0
::/0                           ::                         !n   -1  1  3410 lo

```I hoop that some one can help me with is issue.

---

