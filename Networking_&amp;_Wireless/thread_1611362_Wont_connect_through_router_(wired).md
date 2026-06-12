---
title: "Wont connect through router (wired)"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by Demijinx on 2010-11-01
Hey Im trying to setup Ubuntu for my buddy. After talking it up for ages of course i get a problem ive never seen be for :(. He is running 10.10 (or whatever the newest is lol) and when running windows it hooks up to the internet just fine through the router. however in ubuntu it will only connect when i plug it directly into the modem. Here is some more info

jake@jake-Dell-DXP061:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:b6:67:e0  
          inet6 addr: fe80::216:76ff:feb6:67e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1698068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1205790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:882455042 (882.4 MB)  TX bytes:1262659539 (1.2 GB)
          Interrupt:21 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:162056 (162.0 KB)  TX bytes:162056 (162.0 KB)

jake@jake-Dell-DXP061:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
jake@jake-Dell-DXP061:~$ 


Route gives no output. Kinda weird. router is Linksys Wireless G Broadband Router. WRT54G.

Please help! I dont want him running back to windows before he even gets into it.

---

### Post by Iowan on 2010-11-01
Interface (eth0) has no IP address - **ifconfig -a** will show all interfaces. You can check **lshw -C network** to see more about the interface. As a quick double-check, you can try *sudo dhclient eth0*. Worst case, you'll see something like "No DHCP offers... sleeping".

---

### Post by Demijinx on 2010-11-02
> **Iowan said:**
> Interface (eth0) has no IP address - **ifconfig -a** will show all interfaces. You can check **lshw -C network** to see more about the interface. As a quick double-check, you can try *sudo dhclient eth0*. Worst case, you'll see something like "No DHCP offers... sleeping".

Here is what it spit out

jake@jake-Dell-DXP061:~$ sudo dhclient eth0
[sudo] password for jake: 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:16:76:b6:67:e0
Sending on   LPF/eth0/00:16:76:b6:67:e0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
jake@jake-Dell-DXP061:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:76:b6:67:e0  
          inet6 addr: fe80::216:76ff:feb6:67e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1861110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1248046 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:949860667 (949.8 MB)  TX bytes:1268180497 (1.2 GB)
          Interrupt:21 Memory:dffe0000-e0000000 

eth0:avahi Link encap:Ethernet  HWaddr 00:16:76:b6:67:e0  
          inet addr:169.254.10.33  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:173572 (173.5 KB)  TX bytes:173572 (173.5 KB)

jake@jake-Dell-DXP061:~$ ^C
jake@jake-Dell-DXP061:~$ 



Any thoughts?

---

### Post by Demijinx on 2010-11-02
Bumpity bump bump.

---

### Post by Demijinx on 2010-11-05
Okay, I fixed it. not the right way but it works. I reinstalled Ubuntu and it works now.

---

