---
title: "no wired ethernet connection"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by caddict on 2009-09-27
i've recently upgraded to jaunty...have an ethernet problem carried over from 8.04. 

it's a wired network of three (static ip) computers through a d-link router. this computer running jaunty does not automatically establish a connection on boot-up.

when i upgraded to 8.04 about a year ago, i had some help to figure out a work-around to get connected. it goes like this:

gksudo ifconfig eth0 up hw ether 00:00:00:00:00:bf
then disable networking with the nm applet; then enable networking

this connects me via "auto ethernet". i wrote a little script which i run from the desktop after startup. after a year of connecting like this and two upgrades, it would be nice to find a better solution.

dmesg shows
```
    2.832246] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.832286] 8139cp 0000:02:05.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.837065] 8139too Fast Ethernet driver 0.9.28
[    2.837107] 8139too 0000:02:05.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.838739] eth0: RealTek RTL8139 at 0xa000, 00:00:00:00:00:00, IRQ 23
[    2.838743] eth0:  Identified 8139 chip type 'RTL-8101'
[  292.912869] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  303.040013] eth0: no IPv6 routers present
[  304.868064] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  315.792009] eth0: no IPv6 routers present

```

---

### Post by cariboo on 2009-09-27
Are you editing the MAC address?

---

### Post by caddict on 2009-09-27
not exactly sure what i'm doing...

ifconfig -a shows a MAC address 00:00:00:00:00:bf

```
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:bf  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::200:ff:fe00:bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18194149 (18.1 MB)  TX bytes:1204851 (1.2 MB)
          Interrupt:23 Base address:0xa000 

```

even if i look up the MAC address using windows i get the same result...the card doesn't seem to have a decent MAC address!

---

### Post by caddict on 2009-09-30
does anyone have any ideas why 

(a) i don't get a connection at boot up?
(b) this weird workaround (mac address spoof?) should work to get me connected?

> gksudo ifconfig eth0 up hw ether 00:00:00:00:00:00
then disable networking with the nm applet; then enable networking

i've tried a hundred options (to the point of confusion) to get an automatic connection.

the set up is very simple, interfaces file is good, the nic card works.

```
auto lo
iface lo inet loopback
#address 127.0.0.1
#netmask 255.0.0.0

iface eth0 inet static
	address 10.1.1.4
	netmask 255.0.0.0
	gateway 10.1.1.1

auto eth0
```

maybe i should disable network-manager?

---

### Post by Iowan on 2009-09-30
NM *shouldn't* mess with a connection defined in */etc/network/interfaces* - though it might still "adjust" /*etc/resolv.conf*.

---

