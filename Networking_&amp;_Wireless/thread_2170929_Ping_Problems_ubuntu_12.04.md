---
title: "Ping Problems ubuntu 12.04"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by martin24 on 2013-08-28
Hi People

I hope someone can help here.
I installed Ubuntu 12.04 Server fresh install.  It is connected to a local network 192.168.33.0/24.
I assigned a static IP:
> auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
**        address 192.168.33.250**
        netmask 255.255.255.0
        network 192.168.33.0
        broadcast 192.168.33.255
        gateway 192.168.33.1
        dns-search XXX.co.za
        dns-nameservers 192.168.33.1 41.xxx.xxx.xxx


When I ping a local PC within my network using the IP, I receive a normal responce:
> ping 192.168.33.150
PING 192.168.33.150 (192.168.33.150) 56(84) bytes of data.
64 bytes from 192.168.33.150: icmp_req=1 ttl=128 time=0.679 ms
64 bytes from 192.168.33.150: icmp_req=2 ttl=128 time=0.623 ms
64 bytes from 192.168.33.150: icmp_req=3 ttl=128 time=0.489 ms


But when I ping the same PC using the computer name "Martin-Ltp", it seems as if my ping heads out into the open www, and replies with a different IP:
> ping Martin-Ltp
PING Martin-Ltp.iplan.co.za (196.41.3.18) 56(84) bytes of data.
64 bytes from saXXXXX.xxxx.co.za (196.41.xxx.xxx): icmp_req=1 ttl=52 time=11.5 ms
64 bytes from saXXXXX.xxxx.co.za (196.41.xxx.xxx): icmp_req=2 ttl=52 time=13.9 ms
64 bytes from saXXXXX.xxxx.co.za (196.41.xxx.xxx): icmp_req=3 ttl=52 time=12.2 ms

What an i missing? 
How do I fix this???

Thanks!

---

### Post by bkline on 2013-08-28
You can add this line to the /etc/hosts file:

192.168.33.150 Martin-Ltp

---

### Post by martin24 on 2013-08-28
Thanks for the reply.
Yes it is possible to fix it that way but my problem is this.
I use Cacti to monitor the network and I need to monitor some laptops that has more than one network interface.  Thus breaking my monitoring every time they change from LAN to Wireless.  Some of these machines will also leave the office and head back to the office a month later, causing an IP change on the DHCP server due to the IP release.
Now I can go and setup Static IP's on the Firewall, but please, that's a last last last resort.
Could the problem be on my Firewall Server (Endian)?

---

### Post by martin24 on 2013-08-28
\

---

