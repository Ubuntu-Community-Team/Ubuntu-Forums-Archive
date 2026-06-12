---
title: "network manager losing dns settings"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by pebay1935 on 2010-05-21
Ubuntu 8.04: I'm using a modem with pon and poff if that matters. I enter the dns setting (System->Administration->Network->Network Settings) suggested by namebench and everything works great. But when I drop connection using poff and come back later, the dns settings have reverted to something I entered some time ago. Is this normal behavior? How do I make it keep what I enter? Thanks

Peyton

---

### Post by anomie on 2010-05-21
[QUOTE=pebay1935]How do I make it keep what I enter?[/QUOTE]

There's surely a more elegant approach, but this will certainly do the trick for you -- after configuring your resolvers, run: 
```
$ sudo chattr +i /etc/resolv.conf
```

The file will be immutable, and *no one* (not even root) will be able to edit it without removing the attribute first.

---

### Post by iponeverything on 2010-05-21
> **anomie said:**
> There's surely a more elegant approach, but this will certainly do the trick for you -- after configuring your resolvers, run: 
```
$ sudo chattr +i /etc/resolv.conf
```

The file will be immutable, and *no one* (not even root) will be able to edit it without removing the attribute first.

If you ask me immutability is pretty elegant ;)

---

### Post by wojox on 2010-05-21
You can also edit:

```
gksudo gedit /etc/dhcp3/dhclient.conf
```

And add:

```
prepend domain-name-servers 8.8.8.8, 8.8.4.4;
```

Change the address to whatever you want.

---

