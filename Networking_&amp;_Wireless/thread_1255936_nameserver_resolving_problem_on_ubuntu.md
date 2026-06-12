---
title: "nameserver resolving problem on ubuntu"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-09-02
Hi,

I have 2 nameserver set up in my /resolv.conf
```

192.168.254.3
191.168.1.1
search remote.lan local.lan

```

These are put there by the resolvconf deamon which gets them from dhcp

.3 is the dns for remote.lan
.1 is the dns for local.lan

I have two machines, an, xp and a ubuntu 9.04

From xp machine
----------------
if I ping x.remote.lan I get a reply
if I ping y.local.lan the first dns fails, and it goes to the second as expcted and I get a reply.


From ubuntu machine
---------------------
if I ping x.remote.lan I get a reply
if I ping y.local.lan the first dns fails, it does not even consider the second dns and promptly returns ping: unknown host y.local.lan

The XP behaviour is what is generally expected, but why is ubuntu not doing it.

Thanks.

---

### Post by puppywhacker on 2009-09-02
As I understand DNS is expecting the DNS server to know everything or delegate to the next DNS server. From a resolver point it expects both DNS server to be part of the hierarchy, but in your case they are not related. So the first DNS server will return something like "not found" and than the resolver gives up. The local dns server will only be used if the remote dns server is unavailable

---

### Post by hal10000 on 2009-09-02
the exact syntax for nameserver entries in /etc/resolv.conf is
```
nameserver 192.168.254.3
nameserver 191.168.1.1
search remote.lan local.lan
```

---

### Post by sefs on 2009-09-02
> **hal10000 said:**
> the exact syntax for nameserver entries in /etc/resolv.conf is
```
nameserver 192.168.254.3
nameserver 191.168.1.1
search remote.lan local.lan
```


Yes it is...I actually have that, but I did'nt cut and paste...so thats not the problem.

---

### Post by sefs on 2009-09-02
> **puppywhacker said:**
> As I understand DNS is expecting the DNS server to know everything or delegate to the next DNS server. From a resolver point it expects both DNS server to be part of the hierarchy, but in your case they are not related. So the first DNS server will return something like "not found" and than the resolver gives up. The local dns server will only be used if the remote dns server is unavailable


That makes sense indeed!  Is there anyway to get it to function like windows?

---

### Post by puppywhacker on 2009-09-02
If you control one of the dns servers, you can place add a "referral" to the other dns server for the remote domains. (see link below)

The resolver is built into the libc library, it can ofcourse be changed, but generally it is considered the heart of a unix system

I like the "DNS or LDAP for rocketscientist" from zytrax, they are technically correct and written in a clear way.

[zytrax dns]("http://www.zytrax.com/books/dns/ch2/index.html#queries")

---

### Post by sefs on 2009-09-02
> **puppywhacker said:**
> If you control one of the dns servers, you can place add a "referral" to the other dns server for the remote domains. (see link below)

The resolver is built into the libc library, it can ofcourse be changed, but generally it is considered the heart of a unix system

I like the "DNS or LDAP for rocketscientist" from zytrax, they are technically correct and written in a clear way.

[zytrax dns]("http://www.zytrax.com/books/dns/ch2/index.html#queries")

Would this work?  If i can put a referral that is always guaranteed to be down. Would that force it then to go to the second one in the list?

---

