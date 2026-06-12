---
title: "Static IP for LAN network"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Arukas on 2009-01-19
I am having a problem with connecting Ubuntu 8.10 to my LAN with a static IP address.

here's my /etc/network/interfaces

[PHP]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address 192.168.111.3
     netmask 255.255.255.0
     network 192.168.111.0
     broadcast 192.168.111.255
     gateway 192.168.111.1



[/PHP]

I can't ping the other two computers.  However the other two computers can see each other and but not the Ubuntu 8.10

---

### Post by Arukas on 2009-01-19
I take it back, my computer can ping the Ibex but Ibex can't ping the others.

---

### Post by jonobr on 2009-01-19
hey

Post ifconfig 

then ping your own IP address does that work?

Are you on the same network as the other two machines?

are you using a 192.168.111.X on them?

I ask as most lans operate with 192.168.1.X

SHould work if the other machines have the same 111

---

### Post by Iowan on 2009-01-19
Firewalls?

---

### Post by Arukas on 2009-01-19
I figured out, its not the static IP bug that no one apparently knows about.  I finally found what it is, and its not the problem.  I had some misinformation.

so thanks for the help anyways.

---

