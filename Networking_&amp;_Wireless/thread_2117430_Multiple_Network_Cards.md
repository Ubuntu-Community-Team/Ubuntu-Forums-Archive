---
title: "Multiple Network Cards"
date: 2013-02-18
forum: Networking &amp; Wireless
---

### Post by Kissell on 2013-02-18
I have a Ubuntu 12.04 machine that works just fine...  except I need to add a 2nd network card to it because I want to run a 2nd instance of mysql on the standard port 3306...  so i have two mysql servers on one box with the standard port.

I added the 2nd network card, and "ifconfig -a" shows it exists as eth1 and it has an ip address on the same network as eth0.  But I can only ping the eth0 interface at "10.111.11.100", I can't ping "10.111.11.101" on eth1.  

Do I need to add some permanent routes to the route table on that Ubuntu box to get it to start working?  :confused:

> eth0      Link encap:Ethernet  HWaddr 02:93:08:c0:a1:d5  
          inet addr:10.111.11.100  Bcast:10.111.11.255  Mask:255.255.255.0
          inet6 addr: fe80::93:8ff:fec0:a1d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1200351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:834602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:188261925 (188.2 MB)  TX bytes:1576379965 (1.5 GB)
          Interrupt:27 
 
eth1      Link encap:Ethernet  HWaddr 02:93:08:ea:28:6a  
          inet addr:10.111.11.101  Bcast:10.111.11.255  Mask:255.255.255.0
          inet6 addr: fe80::93:8ff:feea:286a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8566 (8.5 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:28 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96020 (96.0 KB)  TX bytes:96020 (96.0 KB)

route -n
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.111.11.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         10.111.11.1     0.0.0.0         UG    100    0        0 eth0
10.111.11.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.111.11.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

cat /etc/network/interfaces
> # The loopback network interface
auto lo
iface lo inet loopback
 
# The primary network interface
auto eth0
iface eth0 inet static
address 10.111.11.100
netmask 255.255.255.0
gateway 10.111.11.1
 
auto eth1
iface eth1 inet static
address 10.111.11.101
netmask 255.255.255.0

---

### Post by The Cog on 2013-02-18
I'm not sure, but it might be that there's no gateway defined for the second interface.

Actually, I think you could get away with configuring a second IP address on the first ethernet port - you probably don't need a second physical interface. Try this:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.111.11.100
netmask 255.255.255.0
gateway 10.111.11.1

auto eth0:1
iface eth0:1 inet static
address 10.111.11.101
netmask 255.255.255.0
gateway 10.111.11.1
```

---

### Post by Kissell on 2013-02-18
Yeah, I originally tried a second IP on eth0 using eth0:1 as you suggested, cause that's what we've done on a different server...  but it must have had routes added to that server, cause it don't work.  When I try that I can ping the IP on eth0, but can't ping the IP on eth0:1, and can't ssh into either IP.

---

### Post by Kissell on 2013-02-18
I tried adding a default route:
> 
ip route add default via 10.111.11.1 dev eth1


but I instantly lost my ssh session and had to reboot the box to get it back.

---

### Post by Gyokuro on 2013-02-18
> **Kissell said:**
> I have a Ubuntu 12.04 machine that works just fine...  except I need to add a 2nd network card to it because I want to run a 2nd instance of mysql on the standard port 3306...  so i have two mysql servers on one box with the standard port.

I added the 2nd network card, and "ifconfig -a" shows it exists as eth1 and it has an ip address on the same network as eth0.  But I can only ping the eth0 interface at "10.111.11.100", I can't ping "10.111.11.101" on eth1.  

Do I need to add some permanent routes to the route table on that Ubuntu box to get it to start working?  :confused:



route -n


cat /etc/network/interfaces

You forgot the gateway for eth1

---

### Post by Kissell on 2013-02-18
> **Gyokuro said:**
> You forgot the gateway for eth1

I tried it with and without the gateway on eth1, it didn't work either way.

EDIT: Actually when I set the gateway on eth1 I can't ssh into the box on either IP...  I can ping it on the eth0 IP, but can't ping it on eth1's IP, and can't ssh to either IP.

---

### Post by The Cog on 2013-02-18
You might need tcpdump to work out what's going on there. That would be my next step.

---

### Post by sandyd on 2013-02-18
Can you run WireShark on a computer, then try to ping the second network card from the computer, - and then post the relevant output from Wireshark?

Typically - static IPs broadcast out on the subnet that is set. That said - access by devices that are _not_ on the subnet are not possible unless static routes are given to the clients.

Thanks!

---

### Post by Kissell on 2013-02-18
I've been trying to communicate from another machine on the same Class C subnet, if that makes a difference.

Also these machines are VM instances in Amazon EC2....

---

### Post by oldos2er on 2013-02-18
Moved to Networking & Wireless.

---

### Post by Kissell on 2013-02-18
When i have eth1 configured without a gateway and I try to ping from a different machine on the same subnet, it says "Request timeout for icmp_seq 0"

However, while doing a "tcpdump -i eth1" on the host I'm trying to ping, i see the pings coming in:

> tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type EN10MB (Ethernet), capture size 65535 bytes
13:54:38.768702 IP 10.111.11.200 > 10.111.11.101: ICMP echo request, id 41003, seq 0, length 64
13:54:39.769055 IP 10.111.11.200 > 10.111.11.101: ICMP echo request, id 41003, seq 1, length 64
13:54:40.770145 IP 10.111.11.200 > 10.111.11.101: ICMP echo request, id 41003, seq 2, length 64
13:54:41.771134 IP 10.111.11.200 > 10.111.11.101: ICMP echo request, id 41003, seq 3, length 64
13:54:42.773044 IP 10.111.11.200 > 10.111.11.101: ICMP echo request, id 41003, seq 4, length 64
13:54:43.773144 IP 10.111.11.200 > 10.111.11.101: ICMP echo request, id 41003, seq 5, length 64
13:54:44.774195 IP 10.111.11.200 > 10.111.11.101: ICMP echo request, id 41003, seq 6, length 64

---

### Post by Kissell on 2013-02-18
I got it working by following this guide:
[http://randomizedsort.blogspot.com/2012/06/poor-mans-static-ip-for-ec2-aka-elastic.html]("http://randomizedsort.blogspot.com/2012/06/poor-mans-static-ip-for-ec2-aka-elastic.html")

---

