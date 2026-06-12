---
title: "*Only* add Network interface If Exists"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by nottrobin on 2009-04-12
Hiya networking geniuses

Is there any way for me to make Ubuntu set up a network interface only of it exists?

Because network interface eth1 will only be present sometimes. If I add the following to /etc/network/interfaces:

```

auto eth1
iface eth1 inet dhcp

```

Then, if eth1 is not there, /etc/init.d/networking takes ages to start, because it assumes eth1 is there and spends ages trying to assign an IP address.

Can't I do something like:

```

if exists(eth1)
  auto eth1
  iface eth1 inet dhcp
fi

```

?

Ta,
Robin.

---

### Post by nottrobin on 2009-04-12
okay ignore me I'm being a fool. If the interface isn't there it just fails to load it at all, and that's relatively graceful. So it doesn't matter. Can I delete this message?

---

