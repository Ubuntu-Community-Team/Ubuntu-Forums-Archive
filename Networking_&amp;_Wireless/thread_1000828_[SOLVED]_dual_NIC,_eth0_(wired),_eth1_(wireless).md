---
title: "[SOLVED] dual NIC, eth0 (wired), eth1 (wireless)"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by IQRules on 2008-12-03
On the ThinkPad R32, I have 8.10 Intrepid installed.

/etc/network/interfaces,
auto eth0  -- wired
iface eth0 inet dhcp
auto eth1  -- wireless
iface eth1 inet dhcp

Both NIC connect to 192.168.1.0 subnet.

My question is how to autodetect on such condition,
1) if eth0 is wired to a router
2) signal on eth1 is too weak, auto shutdown eth1

I do not like the idea, use sudo ifdown eth1 command manually.
Not all users on this laptop have sudo privilege.

Thanks

---

### Post by iponeverything on 2008-12-03
do a "man interfaces"

near the top of the manpage you see a section with "up flush-mail"

What you can do is very simular -- Assuming that if the wired connection is up -- you want to use it.


```

iface eth0 inet dhcp
up teardown-eth1
down bringup-eth1

```

Where teardown-eth1 is is simple script in your path with "ifdown eth1"
and bringup-eth1 is a simple script in your path with "ifup eth1"

---

### Post by IQRules on 2008-12-03
Thanks, it is very clever. Let me try it.

---

