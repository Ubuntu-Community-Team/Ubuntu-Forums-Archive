---
title: "intermittent Internet on 10.10 Server with Ubuntu Desktop"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by mebunto on 2010-12-30
Hello, I have been running 10.10 server with no GUI for a few months without issue.  I decided to install ubuntu desktop (GUI), because I want to turn it into a media server, and I'm finding that my Internet browsing fails intermittently.  i.e. I can get google.com sometimes and sometimes not.  I have tried traceroute and found that I do not reach my local router on addresses that fail, and yet I get a full trace on addresses that are ok.  Ping tests too.
I remember from some time ago that the GUI may cause a network problem but I'm not sure.
By the way, other computers on the network can access this host through Samba so the NIC is working fine.
Any suggestions as to what's wrong with the network?

---

### Post by PatchesTheCaveman on 2010-12-30
Sorry you're having trouble!

Do me a favor and run the following commands and paste in the results here:
```
ifconfig -a
route
```

Also, is this a wireless connection?  In that case run these commands also:
```
sudo iwconfig
lspci -v
```

Thank you!

---

### Post by mebunto on 2010-12-31
Thanks for the reply.  It's a wired connection - I have two NICS, one for the Internet and the other is a storage LAN.  Here are the results of the commands:
```
mebunto@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:30:48:84:e2:b2
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36078 (36.0 KB)  TX bytes:23317 (23.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:30:48:84:e2:b3
          inet addr:192.168.2.81  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe84:e2b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3316140 (3.3 MB)  TX bytes:235974 (235.9 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5478 (5.4 KB)  TX bytes:5478 (5.4 KB)

mebunto@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
default         192.168.2.80    0.0.0.0         UG    100    0        0 eth1


mebunto@ubuntu:~$ sudo dhclient eth0
[sudo] password for mebunto:
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:30:48:84:e2:b2
Sending on   LPF/eth0/00:30:48:84:e2:b2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.11 from 192.168.0.1
DHCPREQUEST of 192.168.0.11 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.11 from 192.168.0.1
bound to 192.168.0.11 -- renewal in 37020 seconds.
mebunto@ubuntu:~$

```

---

### Post by PatchesTheCaveman on 2010-12-31
Do you know which one is going to the storage LAN?  It's trying to route packets to the Internet to both, which is probably causing your problem.

If eth0 is your connection to the internet run:
```
sudo route del default dev eth1
```

If eth1 is your connection to the Internet run:
```
sudo route del default dev eth0
```

---

### Post by mebunto on 2010-12-31
thanks, will do and I will let you know what's happening.

Don't you ever sleep?  :)

---

### Post by mebunto on 2010-12-31
OK, deleting the route through eth1 fixes it.  But if I reboot then the second route comes back, so how do I make the change permanent?

Thanks very much for the help.

---

### Post by mebunto on 2011-01-01
FIXED!  Edited /etc/network/interfaces

Commented out the line saying "gateway 192.168.2.80"

now netstat-r shows:

```

mebunto@ubuntu:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     *               255.255.255.0   U         0 0          0 eth1
192.168.0.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth1
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```

So the second gateway that was causing the problem is gone and the NAS (Drobo) still works.

---

