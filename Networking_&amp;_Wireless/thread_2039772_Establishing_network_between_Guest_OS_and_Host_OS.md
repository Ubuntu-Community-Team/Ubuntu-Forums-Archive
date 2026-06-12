---
title: "Establishing network between Guest OS and Host OS"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by mathgen on 2012-08-09
Hi

I have installed VMWare Workstation on Ubuntu Linux 12.04. I want to establish network between Guest OS and the Host OS. I should be able to  login to the Virtual Machine I created in VMware from  Host OS which is  Ubuntu.


Host OS -- Ubuntu Linux 12.04

Guest OS -- Oracle Linux 5.8 

Right now, I get below error when trying to connect to Guest OS.

[B] boris@vx100:~$  ssh lx100
ssh: connect to host lx100 port 22: No route to host [/B]

I checked in several places , they say I have to make sure the ip addresses of both Guest and Host OS should be on the same subnet and it will work. But it is not working for me. 

Below is the /etc/hosts entry on Host Ubuntu OS.

boris@vx100:~$ cat /etc/hosts
[COLOR="RoyalBlue"]127.0.0.1	localhost
127.0.1.1	vx100

192.168.74.10   lx100  lx100
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters[/COLOR]

Virtual Machine has Bridged network adapter.

Below is the "ifconfig" command output on both Host OS and Guest OS.

On Host OS.

[COLOR="RoyalBlue"]boris@vx100:~$ ifconfig 

eth0      Link encap:Ethernet  HWaddr 38:60:77:39:24:62  
          inet addr:192.168.74.2  Bcast:192.168.74.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fe600000-fe620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4601263 (4.6 MB)  TX bytes:4601263 (4.6 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.74.1  Bcast:192.168.74.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.211.1  Bcast:172.16.211.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/COLOR]
--------------------------

On Guest OS


[COLOR="Blue"][root@lx100 ~]# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:29:9C:8D:F3  
          inet addr:192.168.74.10  Bcast:192.168.74.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x2024 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5561090 (5.3 MiB)  TX bytes:5561090 (5.3 MiB)
------------------------ 
[/COLOR]

---

