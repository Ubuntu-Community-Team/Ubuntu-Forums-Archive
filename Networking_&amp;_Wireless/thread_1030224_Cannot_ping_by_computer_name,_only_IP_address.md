---
title: "Cannot ping by computer name, only IP address"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by riksweeney on 2009-01-04
Hi,

I'm trying to ping my other Ubuntu computer by its name, I can only only ping it by IP address. i.e.

```
ping ubuntucomp

ping: unknown host ubuntucomp

ping 192.168.0.5

PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
64 bytes from 192.168.0.5: icmp_seq=1 ttl=64 time=1007 ms
```

What do I need to do to allow pinging by name?

Thanks

Richard

Edit:

I've found a solution to this, nevermind :)

---

### Post by Iowan on 2009-01-04
As this is a frequent question, please post your solution. :D

---

### Post by ajmc on 2011-01-02
can you post how you solve the problem?

---

### Post by spiky001 on 2011-01-02
If you add an entry to /etc/hosts ipadd then next to it name of pc, use ```
gksudo gedit /etc/hosts
```

---

