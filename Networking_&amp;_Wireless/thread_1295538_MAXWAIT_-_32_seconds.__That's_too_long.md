---
title: "MAXWAIT - 32 seconds.  That's too long"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by Terc on 2009-10-19
How do I adjust the MAXWAIT?
I have created a bridge to connect 4 NICs to a single IP.

```
auto lo
iface lo inet loopback

auto br0
iface br0 inet static
bridge_ports eth0 eth1 eth2 eth3
address 192.168.1.1
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
```

Now during boot, I have to wait for about 32 seconds with no disk activity.

If I do /etc/init.d/networking restart I see

Waiting for br0 to get ready (MAXWAIT is 32 seconds)

after about that long, the command completes, and my bridge works.  So, if I could adjust the MAXWAIT to much less, I'd at least like to see if it breaks anything.  I'm guessing it's waiting on something it doesn't need to wait on.

---

### Post by Terc on 2009-10-20
Bump.
Perhaps I should have titled the thread - long timeout during bootup while waiting for network devices.

---

