---
title: "Networking failed for no reason"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by shadowblade989 on 2009-10-22
Hello,

I'm using Ubuntu Hardy on my laptop with a wired connection. Today, for no apparent reason, the networking completely stopped working. 

Restarting networking does nothing. Restarting the whole machine does nothing. I'm at a loss.

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.5
netmask 255.255.255.0
gateway 192.168.2.1

```

All of the config information is correct, and like I said, hasn't been changed recently.

---

### Post by Iowan on 2009-10-23
**ifconfig** shows the machine with IP address? Does **ping** work?

---

### Post by shadowblade989 on 2009-10-23
Yep, ifconfig shows an IP (the correct IP from my config), ping fails for both internal and internet targets.

---

### Post by jhouse59 on 2009-10-24
> **Iowan said:**
> **ifconfig** shows the machine with IP address? Does **ping** work?

I'm having the same problem. But, I can ping each machine. There's an icon for my network (which is HOME). Mine would work, but seems like when I done an update. Then it just quit working. Also, mine did work on the wired connection (Laptop). The wireless wouldn't connect to the network. Is there something I need to add to the smb.conf file? To get it to work.

---

### Post by Iowan on 2009-10-24
> **shadowblade989 said:**
> Yep, ifconfig shows an IP (the correct IP from my config), ping fails for both internal and internet targets.
Fails for **ping** by name, by IP address, or both?

---

