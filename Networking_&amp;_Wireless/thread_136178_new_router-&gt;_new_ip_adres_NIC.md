---
title: "new router-&gt; new ip adres NIC?"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by stoeptegel on 2006-02-25
I've got a new router from my ISP today. 

The first thing i did in my browser, was setup the router as static DHCP for LAN, so that my linux and my parents windows box should work ok with NAT.

My problem now with the new router, is that my eth0 NIC on my linux box takes another IP adress than is configures in interfaces.

/etc/network/interfaces```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
address 192.168.1.34
netmask 255.255.255.0
gateway 192.168.1.1
```
 
ifconfig:```

eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:169.254.62.196  Bcast:0.0.0.0  Mask:255.255.0.0

```

Is this me looking triple?

---

### Post by suRoot on 2006-02-25
169.254.62.196 is part of a subnet reserved for automatic IP addressing - meaning, you get that address if either a) you haven't statically assigned one or b) no dhcp server is available to give you one.  Obviously you've assigned one, but the NIC isn't taking it.

Have you tried bringing eth0 down & back up?
```

sudo ifdown eth0
sudo ifup eth0
```

---

### Post by stoeptegel on 2006-02-26
Yes i just did; i have to ifup after boot because internet doesn't work anymore if i don't.

$ sudo ifup eth0
Password:
RTNETLINK answers: Cannot assign requested address

$ sudo ifdown eth0
just works

When i do ifup again i get this and i have to do ifup twice to get internet working:
$ sudo ifup eth0
SIOCSIFADDR: File exists
Failed to bring up eth0

Somehow i'am glad the ip number number makes sense :)

---

### Post by suRoot on 2006-02-26
192.168.1.34 isn't part of your dhcp pool, is it?

---

### Post by stoeptegel on 2006-02-26
Not that i can see, it's unconfigured AFAIK

[img]http://img301.imageshack.us/img301/9012/dhcppool2qs.jpg[/img]

The weird thing is, i have configured the new modem/router the same as the old one. On that the old router 192.168.1.34 worked fine.

---

### Post by stoeptegel on 2006-02-28
If someone has something to share with me about this please, please tell.  I still need a helping hand here.

---

### Post by stoeptegel on 2006-03-01
I came to the conslusion that it is something with my configuration, because a live-cd works perfect.

I've searched a some and will supply some codes i dunno what todo with, but maybe someone here does. :)

Note: i've configured the LAN static by DHCP with mac addresses, instead of fully static.
```

sudo ifdown eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 7943
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/**:**:**:**:**:**
Sending on   LPF/eth0/**:**:**:**:**:**
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
```

```

$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/**:**:**:**:**:**
Sending on   LPF/eth0/**:**:**:**:**:**
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.0 -- renewal in 110019 seconds.
RTNETLINK answers: Cannot assign requested address

```

```

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

```

$ ps aux | grep dhcp
dhcp      9299  0.0  0.1   2336  1176 ?        Ss   08:37   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0
mvv       9599  0.0  0.0   2944   624 pts/5    R+   08:47   0:00 grep dhcp

```

Please guys, help me out here. I don't wanna reinstall (k)ubuntu yet.

---

### Post by stoeptegel on 2006-03-01
I solved it with my best friend google :)
I needed to run 
# dhclient
manually, that's the workaround until i reinstall kubuntu.

---

### Post by stoeptegel on 2006-03-08
Running dhclient seemed buggy for a solution, and i had to reinstall (k)ubuntu. 

IMO the wiki can use information to convert from static etho to working DHCP eth0. If someone knows how to do it, please make a wikipage because having to reinstall ubuntu just because you need the NIC working in DHCP mode instead of static is kind of not newbie friendly i guess.

---

