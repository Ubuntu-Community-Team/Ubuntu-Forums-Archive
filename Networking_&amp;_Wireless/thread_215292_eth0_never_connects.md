---
title: "eth0 never connects"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by WesleyWex on 2006-07-13
My eth0 interface is always disconnected, but the cables and the network card are perfectly ok, and my switch says that there is an online connection with my Ubuntu machine.

What's going on?

I've tried to change my /etc/network/interfaces to look like:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

mapping hotplug
script grep
map eth0

auto eth0
iface eth0 inet static
dns-nameservers 192.168.1.1
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
```

Even when I activate DHCP it takes a long time setting up and no IP is retrieved.

Anyone knows what's wrong?

(it's weird but Ubuntu says there's 129 updates, but without any connection to the internet)

---

### Post by gratefultux on 2006-07-13
What's the output for 'ifconfig'?

---

### Post by WesleyWex on 2006-07-14
I was able to activate the network card searching for davicom, someone should fix it on the alternative install cd, because the desktop cd works...

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

