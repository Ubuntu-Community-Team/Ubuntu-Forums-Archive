---
title: "3com PCMCIA ethernet card problem"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by muleaga on 2006-02-24
Hallo,

I'm trying Breezy (only server mode) on my old laptop (HP Omnibook 900 with 3Com PCMCIA ethernet card model 3CCFEM556B). During installation DHCP configuration was OK, but after reboot there is no connection.

> sudo ifconfig eth0:
**********************************
Link encap: Ethernet HWaddr 00:00:86:33:CD:A2
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:62 errors:0 dropped:0 overruns:0 carrier:47
collisions:0 txqeuelen:1000
RX bytes:0 (0.0 b) TX bytes:724 (724.0 b)
Interrupt:3 Base address:0x300
*********************************

/etc/network/interfaces:
*********************************
auto eth0
iface eth0 inet dhcp
*********************************

> sudo lshw -class network:
*********************************
description: Ethernet interfaces
physical id: 2
logical name: eth0
serial: 00:00:86:33:cd:a2
capabilities: ethernet physical
configuation: broadcast=yes driver=3c571_cs mlticast=yes
*********************************

I added (acpi=off) in grub boot file, but no changes.

Help please...

---

### Post by muleaga on 2006-02-24
Hi.

I get with 'dmesg':

Disabling IRQ #10
eth0: interrupt(s) dropped!

maybe this can help to find the solution.

Anyone?

Thanx.

---

### Post by muleaga on 2006-02-24
Solved it.
Problem was irqpolling.
I just added irqpoll to my grub boot file and everything works fine.

\\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/

---

