---
title: "Iptables: Natting a machine only on external connections"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by Metallion on 2011-03-22
I've got the following two subnets.

```

Subnet 1: 10.1.0.0/24
Subnet 2: 172.16.0.0/24

```

A machine in subnet 1 is natted to a static address in subnet 2. For instance 10.1.0.10 is natted to 172.16.0.10.

I have achieved this with the following iptables rule. (in addition to enabling forwarding)

```
iptables -t nat -A POSTROUTING -s 10.1.0.10 -j SNAT --to 172.16.0.10
```

So far this works perfectly. What I want to do now is to add another rule that only nats the machine in case it is NOT accessing subnet 1.

In other words, when this machine accesses any other machine in subnet 1, it should show up as 10.1.0.10. Whenever it accesses subnet 2 of anything else, it should appear as 172.16.0.10.

Can this be done with iptables? Thanks in advance.

---

### Post by Metallion on 2011-03-22
Never mind, I solved it. This is the rule that does what I want:

```

iptables -t nat -A POSTROUTING ! -d 10.1.0.0/24 -s 10.1.0.10 -j SNAT --to 172.16.0.10

```

---

