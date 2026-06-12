---
title: "Network-manager won't automatically reconnect"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by Syzothermy on 2009-02-05
Whenever I lose a connection, network-manager asks for the key again; kind of annoying for downloading. "connect automatically" doesn't help. Is there any way to force it to reconnect? maybe a different network manager (tried WICD, and it reconnects fine, but disconnects way too frequently)?

I'm using Ubuntu 8.10.. I can give more information if needed.

---

### Post by Syzothermy on 2009-02-21
2 weeks, still no answer :(

The card is an RTL8180 if that helps any..

---

### Post by djsephiroth on 2009-02-23
Haha, welcomne to Ubuntu forums. >_>

Can you paste your /etc/network/interfaces?

Possible solution (but not sure without seeing more info about your setup): [http://www.linuxforums.org/forum/linux-networking/43978-ubuntu-wireless-boot-connect.html](http://www.linuxforums.org/forum/linux-networking/43978-ubuntu-wireless-boot-connect.html)

---

### Post by Syzothermy on 2009-02-24
> **djsephiroth said:**
> Haha, welcomne to Ubuntu forums. >_>

Can you paste your /etc/network/interfaces?

Possible solution (but not sure without seeing more info about your setup): [http://www.linuxforums.org/forum/linux-networking/43978-ubuntu-wireless-boot-connect.html](http://www.linuxforums.org/forum/linux-networking/43978-ubuntu-wireless-boot-connect.html)

it only has 

```
auto lo
iface lo inet loopback

```

It works fine on boot, but overnight it just breaks, I guess. No clue.

Someone on the ubuntu IRC channel taught me how to "fix" the /etc/network/interfaces file, but it ended up not being able to connect at all after I did so, but maybe it was just some wrong syntax or something. So, I deleted it and just went back to what the default was, which is the two lines above.

---

