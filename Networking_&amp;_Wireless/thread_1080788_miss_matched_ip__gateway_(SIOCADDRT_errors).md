---
title: "miss matched ip / gateway (SIOCADDRT errors)"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by champi0n on 2009-02-25
Ok, I'm trying to set up a STATIC ip address that has a miss matched gateway address. (Was getting SIOCADDRT erros and such)

```
auto eth0
iface eth0 inet static
address 192.168.23.161
netmask 255.255.255.248
gateway 82.44.142.92

```

While the above settings are "correct" in theory, it doesn't allow access in or out.

I'm manually able to add routes to make it work:

```

sudo route add -host 82.44.142.92 eth0
sudo route add default gw 82.44.142.92

```

Then I can happily ping the outside world, get incoming connections, all that happy feely stuff.

**But the problem is, how do I add those routes so they stay forever?** When I reboot the system of course my newly added routes don't stick.

---

### Post by champi0n on 2009-02-25
think i figured it out... add the following lines to
/etc/network/interfaces
```

up route add -host 82.44.142.92 eth0
up route add default gw 82.44.142.92

```

---

### Post by champi0n on 2009-02-25
nevermind, that was garbage and didnt work

---

