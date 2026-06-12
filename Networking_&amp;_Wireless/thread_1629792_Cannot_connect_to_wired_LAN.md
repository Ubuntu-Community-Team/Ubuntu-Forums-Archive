---
title: "Cannot connect to wired LAN"
date: 2010-11-24
forum: Networking &amp; Wireless
---

### Post by icekid on 2010-11-24
I cannot connect directly to Internet. I have to run this is terminal

```
sudo dhclient
``` 

only then I can connect to Internet. But if I shut down or restart I cannot connect then. I have to again run dhclient. I am running Ubuntu 10.10

---

### Post by pawhtiobo on 2010-11-24
What configuration do you have in:

[B][I][U][/etc/network/interfaces]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")

[/U][/I][/B]
You should have a line like this:

auto eth0
iface eth0 inet dhcp



See ya...

---

### Post by fallenstar on 2010-11-26
Hi,

I have the same problem, running ubuntu studio 10.10, had no wired at all in my laptop until i saw to type dhclient!

here's my output

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface 
auto eth0
iface eth0 inet dhcp

I used to have wired, to download the wifi broadcom stuff, but haven't tried it since, until router died and wifi from a livebox seems an impossibility.

---

