---
title: "wireless once worked..now nothing....helpp please"
date: 2006-03-21
forum: Networking &amp; Wireless
---

### Post by sherlock-holmes on 2006-03-21
i was happy with breezy for more than 4 months....

then tried dapper and now  back to breezy....

after a dist-upgrade i cant connect to the wireless not even once!!!

here is what i get 

[PHP]name@comp:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 9006
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:12:f0:24:20:2d
Sending on   LPF/eth1/00:12:f0:24:20:2d
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
Trying recorded lease 192.168.1.101
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
connect: Network is unreachable
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
No working leases in persistent database - sleeping.[/PHP]

and my /etc/network/interfaces looks like

[PHP]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth1

iface eth1 inet dhcp
wireless-mode managed
wireless-essid xxxxxxxxx
wireless-key xxxxxxxxxx

auto eth1
[/PHP]


please help.....i tried everything i could....i cant connect/ping anything....

in XP it works fine... wired network works flawlessly....

i didnt have any problem with my card.... and i am using the same network now on XP to write this..... SOS ...!!!!

---

### Post by dbw on 2006-03-21
I recognize those SIOC flags errors.  It seems to me that they are related to not having the wifi kernel module loaded.  You might reload ndiswrapper or madwifi using modprobe.  Alternatively, I was actually able to just past my madwifi files from a working kernel to the one I compiled.  Check the /lib/modules/"kernel" directory.

---

### Post by sherlock-holmes on 2006-03-21
[QUOTE=dbw]I recognize those SIOC flags errors.  It seems to me that they are related to not having the wifi kernel module loaded.  You might reload ndiswrapper or madwifi using modprobe.  Alternatively, I was actually able to just past my madwifi files from a working kernel to the one I compiled.  Check the /lib/modules/"kernel" directory.[/QUOTE]

how do i do those? a step by step instruction would be great... thanks...

---

