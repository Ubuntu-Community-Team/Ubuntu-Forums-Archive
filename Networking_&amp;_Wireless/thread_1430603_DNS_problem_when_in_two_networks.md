---
title: "DNS problem when in two networks"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by keysbr on 2010-03-15
I use two fixed IP networks at once, one has internet access and the other is a local network.
While both networks are conected, my DNS server canot resolve domain names.
When I desconect my local network, the DNS server is able to resolve domain names and gives me internet access.
I have a Windows XP in the same machine and windows works fine with both networks. Also I've tried installing ubuntu 8.04 and 9.10, both gives me the same problem.

---

### Post by Iowan on 2010-03-15
Post results (from a terminal) of **route -n** - either/both networks. Also, how are interfaces configured - Network Manager, */etc/network/interfaces*, or a combination of the two?

---

### Post by pricetech on 2010-03-15
It sounds like it's trying to use the internal network as the default, which won't give you Internet access.  Try manually configuring at least the internal interface and leave the Default Gateway entry blank.

---

### Post by colemar on 2010-04-11
I myself had a similar problem, solved this way:
[http://ubuntuforums.org/showthread.php?p=9106614](http://ubuntuforums.org/showthread.php?p=9106614)

---

