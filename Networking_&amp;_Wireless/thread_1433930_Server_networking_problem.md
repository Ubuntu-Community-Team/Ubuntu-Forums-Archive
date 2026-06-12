---
title: "Server networking problem"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by zdenal on 2010-03-19
Today I have updated kernel of my server from 2.6.31-19 to 2.6.31-20. With this update SAMBA has been already updated.

Since this update all my daemons (HTTP, SSHD) are cut off from my network - connections on those services timeouted.

ping to my server timeouted too.

all daemons are up and running, and available from server terminal  by localhost or fixed IP assigned to network adapter.

IPtables has no config and are stopped. iptables -F doesn't help too.

Outgoing connections are not affected -> is possible to ping outside, download updates etc.. Only Incoming connections are affected.

The worst thing is that booting to older kernel 2.6.31-19 doesn't help now.

Do you have any idea, what happened ?

---

### Post by 666f6f on 2010-03-21
pretty weird.. have you found the cause?

---

