---
title: "Network stops talking to gateway randomly"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by wortmanb on 2009-10-20
I just recently upgraded from 804 to 810, then 810 to 904.  Exceedingly happy except for this one little issue.

I use two NICs in a home media server and use bonding to join them.  This appears to work well except that periodically, without any apparent warning that I can find in the system logs, the system will just stop talking to remote clients.  nslookup won't work, pinging outside the network doesn't work, but SAMBA, VNC, ssh, and other protocols still work on my LAN.

My gateway box is an Astaro Security Gateway computer and all my other machines are able to get through it just fine during these outages.  Often, the network will return to service just as quietly as it went out.

At present, my routing table looks like this:

root@marvin:/usr/src/simplifymedia# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 bond0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth1
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 bond0
default         192.168.1.1     0.0.0.0         UG    100    0        0 bond0

bret@marvin:~$ ifconfig -a
bond0     Link encap:Ethernet  HWaddr 00:c0:ca:14:70:0a  
          inet addr:192.168.1.199  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe14:700a/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:38414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2774657 (2.7 MB)  TX bytes:56042504 (56.0 MB)

eth0      Link encap:Ethernet  HWaddr 00:c0:ca:14:70:0a  
          inet addr:192.168.1.225  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:17442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1283656 (1.2 MB)  TX bytes:28038385 (28.0 MB)
          Interrupt:18 Base address:0x9400 

eth1      Link encap:Ethernet  HWaddr 00:c0:ca:14:70:0a  
          inet addr:192.168.1.239  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:20972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1491001 (1.4 MB)  TX bytes:28004119 (28.0 MB)
          Interrupt:249 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:157281 (157.2 KB)  TX bytes:157281 (157.2 KB)

pan0      Link encap:Ethernet  HWaddr 2e:2d:9c:fb:a0:52  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

bret@marvin:~$


I'm not sure where to start looking for this, and I'm not sure why eth0 and eth1 are showing up as interfaces in the routing table!  Any pointers?

Thanks,


Bret

---

