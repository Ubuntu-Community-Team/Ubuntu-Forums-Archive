---
title: "Have connection but Network Manager shows Disconnected"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by CypherHackz on 2009-08-28
Hi,

System: Ubuntu 9.04

Previously I'm using mobile broadband to connect to the internet. The Network Manager working fine, it can detects my connection when I surf the Internet by using the USB modem.

But after I changed to Wired connection using Wimax modem, the Network Manager cannot detect my connection and I cannot surf the Internet. But after I put the 

```
auto eth0
```

in /etc/network/interfaces, I can surf the Internet, download files, etc.

But the problem is, Network Manager still displays Disconnected icon. An even my IP Address does not shown on my conky. It is like the system cannot detect the assigned IP address eventhough the connection is there.

-cypher.

---

### Post by Iowan on 2009-08-28
Network Manager doesn't touch (or acknowledge?) interfaces configured in */etc/network/interfaces*. Is eth0 configured there - or just the **auto eth0** line?

---

### Post by CypherHackz on 2009-08-29
Yup! It not acknowledged that the connection is already established.

Here is the output from, cat /etc/network/interfaces

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

What I did was just add *auto eth0* above the last line to get the IP address using DHCP. But the Network Manager not detect the connection.

-cypher.

---

### Post by dbalascak on 2009-08-29
> **Iowan said:**
> Network Manager doesn't touch (or acknowledge?) interfaces configured in */etc/network/interfaces*. Is eth0 configured there - or just the **auto eth0** line?

Exactly as Iowan is saying.  There are 2 ways to configure the interface(s) and each one ignores the other( they may cause problems if you use both and supply different configs).

If you configure the */etc/network/interfaces* NM won't know they exist. No big deal. If you configure */etc/NetworkManager/nm-system-settings.conf* to be 

```
[ifupdown]
      managed=true
``` 

NM will see the interfaces and configure them.  
If you want to use NM the */etc/network/interfaces* can be left at the default. 

```
auto lo
      iface lo inet loopback

```

If you have only one interface the simplest is to use the */etc/network/interfaces*. If you want to use NM, it will give you a visible status. 
If you have a laptop and you have a wireless and wired interface NM allows you to switch from the desktop. This is where NM really shines.

---

### Post by CypherHackz on 2009-08-29
Thanks! Now I'm understand. The NM is working now.
Thanks to you both.

-cypher.

---

