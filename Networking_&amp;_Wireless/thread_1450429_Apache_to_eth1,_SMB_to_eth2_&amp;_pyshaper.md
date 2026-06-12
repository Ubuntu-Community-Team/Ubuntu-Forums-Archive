---
title: "Apache to eth1, SMB to eth2 &amp; pyshaper?"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by mod on 2010-04-09
Hello,

I'm having some routing problems. I'd want to:

1) Run apache on 172.16.1.131 (Limited to 512kbps with pyshaper) (eth1)
2) Run samba & apache locally on 172.16.1.11 (eth2)

But all the traffic always goes via eth2, and is limited to ~200 KB/s.

Any help..? My routing is all wrong? DD-WRT gives DMZ to 172.16.1.131

**route -n**
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.1.0      *               255.255.255.0   U     0      0        0 eth2
172.16.1.0      *               255.255.255.0   U     0      0        0 eth1
default         DD-WRT          0.0.0.0         UG    0      0        0 eth2

**ifconfig**
> eth1      Link encap:Ethernet  HWaddr 00:21:27:c4:94:c2
         inet addr:172.16.1.131  Bcast:172.16.1.255  Mask:255.255.255.0
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:377407 errors:0 dropped:0 overruns:0 frame:0
         TX packets:999327 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:27325781 (27.3 MB)  TX bytes:733664529 (733.6 MB)
         Interrupt:23 Base address:0xb400

eth2      Link encap:Ethernet  HWaddr 00:06:4f:38:27:69
         inet addr:172.16.1.11  Bcast:172.16.1.255  Mask:255.255.255.0
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:124772 errors:0 dropped:0 overruns:0 frame:0
         TX packets:251619 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:15509742 (15.5 MB)  TX bytes:355229047 (355.2 MB)
         Interrupt:22 Base address:0xc00

lo        Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:77 errors:0 dropped:0 overruns:0 frame:0
         TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:8888 (8.8 KB)  TX bytes:8888 (8.8 KB)

**ip addr**
> 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
   link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
   inet 127.0.0.1/8 scope host lo
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
   link/ether 00:18:f3:09:37:74 brd ff:ff:ff:ff:ff:ff
3: eth2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc htb state UP qlen 1000
   link/ether 00:06:4f:38:27:69 brd ff:ff:ff:ff:ff:ff
   inet 172.16.1.11/24 brd 172.16.1.255 scope global eth2
4: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc htb state UP qlen 1000
   link/ether 00:21:27:c4:94:c2 brd ff:ff:ff:ff:ff:ff
   inet 172.16.1.131/24 brd 172.16.1.255 scope global eth1
5: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN
   link/ether da:5d:bd:5c:04:89 brd ff:ff:ff:ff:ff:ff



**ip addr**
> # time period in seconds between each run
period 10

eth2.ip 172.16.1.11
eth2.in 2048
eth2.out 2048

eth1.ip 172.16.1.131
eth1.in 512
eth1.out 512

 # traffic class 'http' on interface 'eth1'
 eth1.http.in 256
 eth1.http.out.ceil 256
 eth1.http.out.rate 128
 eth1.http.pri 5

 # traffic class 'default' on interface 'eth1'
 eth1.default.in 512
 eth1.default.out.rate 63
 eth1.default.out.ceil 64
 eth1.default.pri 10


**netstat -natp**
> Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address
State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*    LISTEN      2833/mysqld
tcp        0      0 172.16.1.11:139         0.0.0.0:*    LISTEN      28139/smbd
tcp        0      0 172.16.1.131:80         0.0.0.0:*    LISTEN      30894/apache2
tcp        0      0 0.0.0.0:22              0.0.0.0:*    LISTEN      12363/sshd


---

