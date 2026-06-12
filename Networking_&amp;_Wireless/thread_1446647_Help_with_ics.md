---
title: "Help with ics"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by stilling on 2010-04-04
so what i did

eth0 = pppoe internet connection
eth1 = lan connection

i opend terminal logged in as superuser and done this

ifconfig eth1 192.168.0.1

iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

echo 1 > /proc/sys/net/ipv4/ip_forward

apt-get install dnsmasq

/etc/init.d/dnsmasq restart

ifconfig eth1 192.168.0.1

iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

/etc/sysctl.conf

where i added net.ipv4.ip_forward = 1


my PROBLEM

after reboot pppoe connection did not start at boot
so i opened terminal and sudo pon dsl-provider to bring up the pppoe connection again

and on the other computer with windows no internet 

so what is not good and what can i do to be all OK


Thanks in advance

---

### Post by Bachstelze on 2010-04-04
Did the connection sharing work before you rebooted?

---

### Post by stilling on 2010-04-04
pppoe connection when i did tha pppoeconf worked smooth no problems

and no does not work before reboot

---

### Post by stilling on 2010-04-04
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:27:19:b5:93:2d  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::227:19ff:feb5:932d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11743 (11.7 KB)  TX bytes:5111 (5.1 KB)
          Interrupt:16 Base address:0xdf00 

eth1      Link encap:Ethernet  HWaddr 00:0f:1f:93:08:56  
          inet6 addr: fe80::20f:1fff:fe93:856/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4677 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:4619669 (4.6 MB)  TX bytes:815846 (815.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:209476 (209.4 KB)  TX bytes:209476 (209.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:188.27.189.54  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:202980 (202.9 KB)  TX bytes:81117 (81.1 KB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:188.26.167.145  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:439 errors:0 dropped:0 overruns:0 frame:0
          TX packets:505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:200163 (200.1 KB)  TX bytes:85667 (85.6 KB)

---

### Post by Bachstelze on 2010-04-04
I use [this guide](http://www.gentoo.org/doc/en/home-router-howto.xml) when I need to setup connection sharing on Linux. It works on any distro, just skip the Gentoo specifics like compiling the kernel and suchlike.

---

### Post by stilling on 2010-04-04
i SOLVED IT 

with 
sudo poff -a
sudo /etc/init.d/networking restart
internet on the both workes smooth



Thanks so much for your quick answer!!!


Tkans GOD for UBUNTU

---

