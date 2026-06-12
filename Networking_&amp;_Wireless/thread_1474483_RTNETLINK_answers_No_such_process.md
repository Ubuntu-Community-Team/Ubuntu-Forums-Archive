---
title: "RTNETLINK answers: No such process"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by lo.j on 2010-05-06
hi all,

```
/etc/init.d/networking restart
``` gives me the warning in the subject: "RTNETLINK answers: No such process".

i'd like to know what's wrong with my **/etc/network/interfaces**:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0

auto eth1
iface eth1 inet static
        address 10.0.0.1
        netmask 255.0.0.0

up route add default gw 192.168.0.1

```

though the warning is bothersome, i'd like to point out that all works anyway...
thank you.

---

### Post by lo.j on 2010-05-06
any suggestion?
thanks...

---

### Post by lo.j on 2010-05-09
i'd just like to know if my interfaces file is correct,
thanks...

---

### Post by Iowan on 2010-05-09
Dunno if it'll make any difference, but you might try:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        gateway 192.168.0.1

auto eth1
iface eth1 inet static
        address 10.0.0.1
        netmask 255.0.0.0


```

---

### Post by lo.j on 2010-05-09
hi and thanks for the replay :)

i've already tried with no route rule.
no success, even if i need the default route to be set...

---

### Post by Iowan on 2010-05-09
Did you try setting up the static addresses via Network Manager? (NM seems to be getting a bit more possessive as it evolves.)

---

