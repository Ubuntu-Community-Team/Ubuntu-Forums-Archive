---
title: "Multiple ISP"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by SiN486 on 2010-01-13
I have two NICs that go to two different internet connections, and one 'out' NIC. What I want is the users on the 'out' interface to be automatically directed to one or the other internet connection.

For instance: gaming traffic will go through the first internet connection, and downloading traffic will go through the other internet connection.

I'm setting up a ubuntu server box with 3 NICs, can someone give me a general rundown of how to do this, or at least point me in the right direction.

```

INTERNET via NIC 1 -----
                        \
                         \
                          UBUNTU BOX ------ NIC 3 ------- USERS
                         /
                        /
INTERNET via NIC 2------
```

---

### Post by shredder12 on 2010-01-13
I don't know the exact way to do so.. but just to give an idea. You can forward the packets related to some specific ports (for gaming) on one interface and the rest on another. 

I think this can be done this using firewall(iptables).

---

### Post by sanderj on 2010-01-13
See here: [https://help.ubuntu.com/community/InternetAndNetworking/DualHomedGatewayDHCP](https://help.ubuntu.com/community/InternetAndNetworking/DualHomedGatewayDHCP)

---

