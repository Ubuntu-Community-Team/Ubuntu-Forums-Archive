---
title: "virtual interface not up at boot time"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by bigheart on 2009-08-03
Hi i configured a virtual interface in /etc/network/interface like below;

auto lo
iface lo inet loopback


auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
	address 192.168.1.10
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1


auto eth0:1
iface eth0:1 inet static
	address 192.168.1.20
	netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

however, after the system reboot, only the eth0 was up but eth0:1 is not.
i can bring eth0:1 up by ifconfig etho0:1 192.168.1.29 up.

what i missed or do wrong so the eth0:1 not up at the boot time?

thanks for your help!

Joseph

---

