---
title: "how to enable internet access"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by true_friend on 2006-07-13
i configured my internet connection with dhcp. the ip address, the default gateway and the netmask 255.255.255.0 etc.
my sys is kubuntu 6.06. now i can not open the internet traffic. messenger or website. it simply mean althoug network is enabled but still no access to internet through my server.
DSL connection is used by our cable net server.
can any one help me in this regard???

---

### Post by elettronicha on 2006-07-13
does the dhcp release an IP? try the command 'ifconfig'.

---

### Post by true_friend on 2006-07-13
thnx for reply. i provide its out put in both cases

---

### Post by true_friend on 2006-07-13
ipconfig is not working. bash command not fount error is returned. more i m using static ip address assigned manually.if i get it auto matic network stops working.

---

### Post by elettronicha on 2006-07-14
It's 'ifconfig' not 'ipconfig' (like in windows).

Are you sure your router or your internet provider support dhcp?

---

### Post by true_friend on 2006-07-14
it is static ip address which is provided to me. out put of xp 2006 system is given
................................
Physical Address: 00-20-ED-2C-EF-48
IP Address: 192.168.0.139
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.0.1
DNS Server: 192.168.0.1
WINS Server: 
..................................
there is a DNS server also. but there is no option of DNS server in Kde networks settings manager. 
[http://ubuntuforums.org/showthread.php?t=210693](http://ubuntuforums.org/showthread.php?t=210693) here also some DNS is discussed about ubuntu. it is gnome Desktop env. but how can in kde??

---

### Post by true_friend on 2006-07-15
The outout from all relative commands. what is ur guess about it???
IFCONFIG:::::::::::
eth0      Link encap:Ethernet  HWaddr 00:20:ED:2C:EF:48
          inet addr:191.168.0.139  Bcast:191.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe2c:ef48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:396504 (387.2 KiB)  TX bytes:8664 (8.4 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:21071 (20.5 KiB)  TX bytes:21071 (20.5 KiB)
.................................................................................................
ROUTE::::::::::
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
191.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         191.168.0.1     0.0.0.0         UG    0      0        0 eth0
................................................................................................
IWCONFIG::::::::::
o        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
................................................................................................

PING::::::::::::::
From 191.168.0.139 icmp_seq=6 Destination Host Unreachable
......................................................................................................
in /etc/resolv.conf file there was nothing i added only that line i.e. nameserver 192.168.0.1
.......................................................................................................................
/etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 191.168.0.139
netmask 255.255.255.0
gateway 191.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
............................................................

---

### Post by GnomicGhost on 2006-07-15
Your IP address and gateway is 191.***.***.*** as you have it there.
It should be 192.168.0.1 for the gateway.
I don't think (from memory) that the IP matter in linux like it does in Windows.  But, set you static IP to:
192.168.0.10  <-- IP address
255.255.255.0  <-- Mask
192.168.0.1  <-- Gateway

Hope that helps..?

---

### Post by true_friend on 2006-07-15
it was wrong and i corrected it to 192.********* even it did not worked. my static ip is 192.168.0.139..
i post once again the output

---

### Post by true_friend on 2006-07-16
after correcting ip mistake i can connect to server and ping it but could not internet. tried pinging a website by ip and by [www.something.com](www.something.com)  not reachable returned.
the outputs once again.
...................................................................
 
sameel@sameel-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:20:ED:2C:EF:48
          inet addr:192.168.0.139  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31596 (30.8 KiB)  TX bytes:1754 (1.7 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)


.................................................................................................
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

................................................................................................
o        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
................................................................................................

ameel@sameel-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=128 time=1.44 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=128 time=0.247 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=128 time=0.266 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=128 time=0.263 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=128 time=0.267 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=128 time=0.267 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=128 time=0.256 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=128 time=0.277 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=128 time=0.530 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=128 time=0.461 ms
64 bytes from 192.168.0.1: icmp_seq=11 ttl=128 time=0.650 ms

--- 192.168.0.1 ping statistics ---
11 packets transmitted, 11 received, 0% packet loss, time 10000ms
rtt min/avg/max/mdev = 0.247/0.448/1.449/0.342 ms
..................................................................................................
/etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.0.139
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
........................................................................................
and /etc/resolv.config
name server 162.168.0.1 the only line.
.................................................................

---

