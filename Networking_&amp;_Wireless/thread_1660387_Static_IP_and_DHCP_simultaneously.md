---
title: "Static IP and DHCP simultaneously?"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by Dwebtron on 2011-01-05
Where I work we use almost exclusively Ubuntu 8.04 in command-line only form. I need to know if it is possible to configure one of these devices to use DHCP and a given Static IP at the **same time**. I know how to do one, or the other, but not both. 

#1. Is this possible? 
#2. If so, how?


P.S. Yes, I did look around before I asked this, but I could not find anything. Maybe I suck at searching?

---

### Post by Joe of loath on 2011-01-05
Just to clarify, you mean to use DHCP, but to use the same IP every time?

AFAIK that's something you'd need to do server-side, although I'm not quite sure how.

---

### Post by Dwebtron on 2011-01-05
For example, in the "interfaces" file, we have:

[I]auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp
[/I]

To make this static, the "dhcp" is changed to static, like so:

[I]auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.0
[/I]


My question is.... can these both be set at the same time, so that if one does not work it fails over to the other setting?

---

### Post by bab1 on 2011-01-05
> **Dwebtron said:**
> For example, in the "interfaces" file, we have:

[I]auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp
[/I]

To make this static, the "dhcp" is changed to static, like so:

[I]auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.0
[/I]


My question is.... can these both be set at the same time, so that if one does not work it fails over to the other setting?

No. You have to pick one or the other.

---

### Post by cd-r80 on 2011-01-05
Make a virtual interface. Ifconfig eth0:1 and set it static.

---

