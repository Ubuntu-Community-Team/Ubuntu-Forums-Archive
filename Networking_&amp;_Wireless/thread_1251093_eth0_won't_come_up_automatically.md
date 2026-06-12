---
title: "eth0 won't come up automatically"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by Mark224 on 2009-08-27
I am trying to get my ethernet to work at boot time.  I do have
"auto eth0" in /etc/network/interfaces but "ifup -a" does not start it.  It does start if I run "ifup eth0".

Here is the /etc/network/interfaces:
```

auto eth0
iface eth0 inet static
address 192.168.1.11
gateway 192.168.1.1
netmask 255.255.1.0
network 192.168.1.0
broadcast 192.168.1.255

```

Please advise.

---

### Post by Mark224 on 2009-08-27
I found the problem.  There was a ifconfig eth0 down in /etc/rc.local

---

