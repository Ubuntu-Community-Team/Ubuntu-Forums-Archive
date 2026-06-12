---
title: "Cant connect to WRT54GL router, please help"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by WoXa on 2009-08-12
right, i bought WRT54GL router, i plug one end of a cable to laptop and the other to port nr 1 on router. network manager says: "requesting a network address from the wired network" and after couple sec goes away.. than i change IP by doing this in terminal:

Code:
ifconfig eth0 192.168.1.2 netmask 255.255.255.0

than double check (ifconfig):

eth0      Link encap:Ethernet  HWaddr 00:16:36:a1:8e:bd  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fea1:8ebd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:31270 (31.2 KB)  TX bytes:16966 (16.9 KB)
          Memory:54000000-54020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1693947 (1.6 MB)  TX bytes:1693947 (1.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:bb:b1:4e  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:febb:b14e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104142981 (104.1 MB)  TX bytes:13096855 (13.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-BB-B1-4E-31-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


than i go to firefox and type 192.168.1.1 in, i get no setup. what am i doing wrong or what else can i do to access the setup of my WRT54GL?

thank you very much in advance.

---

### Post by tomBorgia on 2009-08-12
Hi,

When your typing in 192.168.1.2 into firefox thats the IP address you set your pc to with the ifconfig command.

Do a "sudo dhclient" and your pc should get an address from your router... then try to connect to it.

---

### Post by regala on 2009-08-12
> **WoXa said:**
> right, i bought WRT54GL router, i plug one end of a cable to laptop and the other to port nr 1 on router. network manager says: "requesting a network address from the wired network" and after couple sec goes away.. than i change IP by doing this in terminal:

Code:
ifconfig eth0 192.168.1.2 netmask 255.255.255.0

than double check (ifconfig):

eth0      Link encap:Ethernet  HWaddr 00:16:36:a1:8e:bd  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fea1:8ebd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:31270 (31.2 KB)  TX bytes:16966 (16.9 KB)
          Memory:54000000-54020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34607 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1693947 (1.6 MB)  TX bytes:1693947 (1.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:bb:b1:4e  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:febb:b14e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104142981 (104.1 MB)  TX bytes:13096855 (13.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-BB-B1-4E-31-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


than i go to firefox and type 192.168.1.2 in, i get no setup. what am i doing wrong or what else can i do to access the setup of my WRT54GL?

thank you very much in advance.

if you don't have a webserver running on your machine, it is quite normal: 192.168.1.2 is your machine address, not your router's, which may be 192.168.1.1.

the real problem is that such a setup is stupid: putting your two interfaces on the same subnetwork (which is what you have, wlan0 and eth0 on the same lan) is useless, because you have 2 network routes set up (/sbin/route -n) to route to that particular network, and the network layer will ALWAYS select the one from the first route in the routes table.

bear in mind: putting 2 interfaces of a very same machine on the same lan is useless (unless you bond one to another which is not what you did =))

---

### Post by WoXa on 2009-08-12
oh sorry mate, my bad :) its supposed to be 192.168.1.1 in firefox :) its just a writing mistake :P I will try what u just suggested. the idea was to make a same subnet.

---

### Post by WoXa on 2009-08-12
this is what i get after i dhclient:

DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
send_packet: Network is down
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 16
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on vboxnet0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


and tried disabling wireless so after ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:16:36:a1:8e:bd  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fea1:8ebd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:35263 (35.2 KB)  TX bytes:11702 (11.7 KB)
          Memory:54000000-54020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13839 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:665447 (665.4 KB)  TX bytes:665447 (665.4 KB)

pan0      Link encap:Ethernet  HWaddr e2:e1:a7:83:0c:da  
          inet6 addr: fe80::e0e1:a7ff:fe83:cda/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2862 (2.8 KB)

still cant connect to router :(

---

### Post by tomBorgia on 2009-08-12
Your router is set up from factory to just work - i.e. it's not had it's settings changed so it won't DHCP?
If the router is 2nd hand it might be oddly configured so you might need to factory-reset it.

Could be a problem with the cable?

---

### Post by tgalati4 on 2009-08-12
I thought the newer routers connected to 192.168.1.254 for admin work.

---

### Post by WoXa on 2009-08-12
tried different cable, didn't help, resetting didn't help and 192.168.1.254 is not letting me in :(

---

### Post by tgalati4 on 2009-08-12
Try 10.10.0.254 or 10.10.1.254.  I set up a wrt54gl for a neighbor and I believe it chose the 10.x network to avoid conflicts.

---

### Post by WoXa on 2009-08-16
this is just freaking useless... i dont get it, nothing works. could someone please write a step by step how am i supposed to go into WRT54GL configuration page? please please please :(

---

