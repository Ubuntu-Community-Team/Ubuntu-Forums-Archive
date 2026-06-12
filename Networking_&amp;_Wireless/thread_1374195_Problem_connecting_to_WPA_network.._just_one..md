---
title: "Problem connecting to WPA network.. just one."
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2010-01-06
Good afternoon. I am attempting to trouble shoot connecting to a WPA network which I have access too. Whenever I attempt to connect to the wireless network, the little Network Manager sits and spins. After a while, it pops up again asking for my password. 

I am sure I have the correct password, as other laptops are able to connect to the network. I have also rebooted this computer into windows, and have been able to connect to the network. For whatever reason, Linux just won't hook. I can connect straight to the wireless router via ethernet cable with no problems. 

I'm using a Dell 14 with a Intel 3945 card. I also tried my Ralink USB card, and had the same results. I've tried the below with the following results. Can someone help me? 
```

whisper@Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:57:9d:e1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:22:5f:f5:91:d2  
          inet6 addr: fe80::222:5fff:fef5:91d2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:429
          TX packets:25 errors:40 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3375 (3.3 KB)  TX bytes:3575 (3.5 KB)
          Interrupt:17 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:25:64:57:9d:e1  
          inet addr:169.254.9.204  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:29 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr b2:73:a7:69:49:08  
          inet6 addr: fe80::b073:a7ff:fe69:4908/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:6741 (6.7 KB)

pan0:avahi Link encap:Ethernet  HWaddr b2:73:a7:69:49:08  
          inet addr:169.254.5.73  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1



whisper@Laptop:~$ sudo dhclient -r
There is already a pid file /var/run/dhclient.pid with pid 2438
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/b2:73:a7:69:49:08
Sending on   LPF/pan0/b2:73:a7:69:49:08
Listening on LPF/eth1/00:22:5f:f5:91:d2
Sending on   LPF/eth1/00:22:5f:f5:91:d2
Listening on LPF/eth0/00:25:64:57:9d:e1
Sending on   LPF/eth0/00:25:64:57:9d:e1
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

whisper@Laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
Listening on LPF/pan0/b2:73:a7:69:49:08
Sending on   LPF/pan0/b2:73:a7:69:49:08
Listening on LPF/eth1/00:22:5f:f5:91:d2
Sending on   LPF/eth1/00:22:5f:f5:91:d2
Listening on LPF/eth0/00:25:64:57:9d:e1
Sending on   LPF/eth0/00:25:64:57:9d:e1
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Update: Well, I can get my Ralink USB to connect now, but for whatever reason, my internal card won't work. Any thoughts on this matter?

---

### Post by Whisp3r on 2010-01-06
I switched over to WICD, and tried connecting. Almost instantly after putting my password it, it responds "Unable to get IP address." 

Again, any help you guys can provide would be graciously accepted. :)

---

### Post by yumgnomeandthensome on 2010-01-07
I too have switched to 'wcid' and sometimes it is connected on booted up and other times fails to get ip address.
I"m thinking to just statically assign an ip address now (or try another linux strain)

going to try watching what happens when it fails, however im not holding my breath

sudo tail -vf /var/log/messages /var/log/syslog

---

