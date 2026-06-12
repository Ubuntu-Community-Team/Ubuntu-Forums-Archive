---
title: "DHCP client request wrong address"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by ___Kevin___ on 2011-11-18
Hi,

I have configured my router to always assign the same IP address to my computer via DHCP. Running dhclient manually works as expected. But after system restart, NetworkManager always request a wrong ip adress.

after reboot, syslog says:
> 
Nov 18 12:20:45 kevin NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Nov 18 12:20:45 kevin dhclient: Listening on LPF/eth0/00:19:d1:2a:7e:7b
Nov 18 12:20:45 kevin dhclient: Sending on   LPF/eth0/00:19:d1:2a:7e:7b
Nov 18 12:20:45 kevin dhclient: Sending on   Socket/fallback
Nov 18 12:20:47 kevin dhclient: DHCPREQUEST of 192.168.1.104 on eth0 to 255.255.255.255 port 67
Nov 18 12:20:47 kevin dhclient: DHCPACK of 192.168.1.104 from 192.168.1.1
Nov 18 12:20:47 kevin dhclient: bound to 192.168.1.104 -- renewal in 825868400 seconds.


if I run dhclient manually afterwards:

> 
kevin@kevin:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/vboxnet0/0a:00:27:00:00:00
Sending on   LPF/vboxnet0/0a:00:27:00:00:00
Listening on LPF/eth0/00:19:d1:2a:7e:7b
Sending on   LPF/eth0/00:19:d1:2a:7e:7b
Listening on LPF/virbr0/96:b0:89:a4:18:a8
Sending on   LPF/virbr0/96:b0:89:a4:18:a8
Sending on   Socket/fallback
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on virbr0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.40 from 192.168.1.1
DHCPREQUEST of 192.168.1.40 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.40 from 192.168.1.1
bound to 192.168.1.40 -- renewal in 825867407 seconds.


The same happens when I disconnect from any VPN connection. Upon disconnect, the same wrong address (192.168.1.104) is being assigned to eth0 and I have to manually run dhclient -r.

Where does NetworkManager/dhclient store the bad IP address? What can I do to make it just do a normal DHCP request?

Thanks,

Kevin

---

### Post by praseodym on 2011-11-18
Hi,

if your router should send always the same IP address, this one should be outside of the DHCP range of the router.

---

### Post by jonobr on 2011-11-18
very stupid question on my part,

If you want the machine to get the same IP address the whole time,
why not set the machine on a static IP address and remove it from the router as part of the range.

On my setup I allcate part of the range for DHCP

i.e.
192.168.1.2 to 192.168.1.200 for DHCP
And the remainder 192.168.1.201-254 for Static assignment

---

### Post by ___Kevin___ on 2011-11-18
Thanks for your answers. The routers DCHP address range is outside of my pseudo-static IP. I don't want to set eth0 to a real static IP. There must be a place, where Ubuntu's networkmanager or something is storing the wrong IP that is requested.

---

### Post by jonobr on 2011-11-18
Is there something in
/etc/NetworkManager/NetworkManager.conf
which is configured with 192.168.1.104

---

### Post by ___Kevin___ on 2011-11-20
No, there is no such file. There is /etc/NetworkManager/nm-system-settings.conf which is almost empty.

---

