---
title: "how to set two networks working on ubuntu 8.04 server"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by raullmadrid on 2009-04-20
hi

in shotrly i need to setting my eth0 and eth1 with a diffrant ip address and work each two of them with specific host name adderss for request specific port

for example i've program set with port 5000 and another program with 6000 .. so .. now i need to make the eth0 working on the program with port 5000 and the network eth1 working with the port 6000


my setting is like that but i see only the program with port 5000 on eth0 working and the another doesnt working ( i've forwarding ports in each two routers )

```
auto eth0
iface eth0 inet static
address 192.168.1.107
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.249

auto eth1
iface eth1 inet static
address 192.168.15.5
netmask 255.255.255.0
gateway 192.168.15.1
network 192.168.15.0
broadcast 192.168.15.255
```

please i need some support i'm need in this

thanks

---

### Post by Iowan on 2009-04-20
Post results of **ifconfig -a**.

---

### Post by raullmadrid on 2009-04-21
```
root@ubuntu2:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:4d:7c:53:4f
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe7c:534f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7711 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7763 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1316370 (1.2 MB)  TX bytes:937368 (915.3 KB)
          Interrupt:17 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:50:bf:79:44:bd
          inet addr:192.168.15.5  Bcast:192.168.15.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:336 (336.0 B)  TX bytes:336 (336.0 B)
```

---

### Post by dmizer on 2009-04-21
Do you have two routers: one router on 192.168.1.x and one router on 192.168.15.x?

How do you have your network physically connected?

---

### Post by Odemia on 2009-04-21
Looks like there is no traffic on the 192.168.15.5 interface.  More info on the physical setup would help.  Can you tell use what programs you are running?  How is the program not working?  Is it a server that is not responding or a client not able to initiate?  Some programs can be told what interface to use.

If you haven't already do a ping to each router and then to something on he other side of the router.  Which pings work?  Which don't?  You could also try using traceroute, depending on the setup everything may be resolving to go through eth0.

---

### Post by raullmadrid on 2009-04-21
> **dmizer said:**
> Do you have two routers: one router on 192.168.1.x and one router on 192.168.15.x?

How do you have your network physically connected?

yes i do .. 

yes its connected wired

---

### Post by raullmadrid on 2009-04-21
> **Odemia said:**
> Looks like there is no traffic on the 192.168.15.5 interface.  More info on the physical setup would help.  Can you tell use what programs you are running?  How is the program not working?  Is it a server that is not responding or a client not able to initiate?  Some programs can be told what interface to use.

If you haven't already do a ping to each router and then to something on he other side of the router.  Which pings work?  Which don't?  You could also try using traceroute, depending on the setup everything may be resolving to go through eth0.


yes problem i noticed that no traffic on the second network all traffic came on the first primary network .. 

i'm using binary CCcam.x86 and its couldnt ask me for selecte which network i prefer because its a binary file i think ..

i've running two bin CCcam1.x86 and CCcam2.x86 in the config file on /var/etc/CCcam1.cfg for CCcam1.x86 the port for incomming clients connections is 5000 , in the config file on /var/etc/CCcam2.cfg for CCcam2.x86 port is 6000

and port 5000 opened on router 192.168.1.1 .. and the port 6000 opened on router 192.168.15.1 

and each of two routers has diffrant sprated hostname ( dns )

---

### Post by raullmadrid on 2009-04-21
sorry i have not understand what do mean with traceroute .. is that program can make each of proccess working on spicific network ?

---

### Post by raullmadrid on 2009-04-21
i still need support

---

### Post by ionoff on 2009-04-21
Since your using different ports/ranges to determine the route go, example 2 at [http://www.linuxhorizon.ro/iproute2.html](http://www.linuxhorizon.ro/iproute2.html) would be your best bet.

```

Second example:
Goal: To route the packets having the destination port 22/tcp to the RDS and 80/tcp to 
the ASTRAL (no matter what network generates them).
This example it is almost the same as the first one except that we will use iptables to 
mark the packets.

Same chart...

                                                                   ________
                                           +-------------+        /
                                           |    ISP 1    |       /
                             +-------------+    (RDS)    +------+
                             |             | gw 10.1.1.1 |     /
                      +------+-------+     +-------------+    / 
+----------------+    |     eth1     |                       /
|                |    |              |                      |
| Local networks +----+ Linux router |                      |  Internet cloud
|                |    |              |                      |
+----------------+    |     eth2     |                       \
                      +------+-------+     +-------------+    \
                             |             |    ISP 2    |     \
                             +-------------+  (ASTRAL)   +------+
                                           | gw 10.8.8.1 |       \
                                           +-------------+        \________


Same /etc/iproute2/rt_table content:

#
# reserved values
#
255     local
254     main
253     default
0       unspec
#
# local
#
#1      inr.ruhep
1 RDS
2 ASTRAL

Before you start check your iptables configuration. I strongly recommend to read about 
iptables if you are unsure about what you will doing next.
For more documentation go to iptables home page or you can download a good documentation 
from this site (Security & Privacy Section) or directly from here.

To mark the packets that have the 22 and 80 as destination port we will use the 
MANGLE table...

iptables -A PREROUTING -t mangle -i eth0 -p tcp --dport 22 -j MARK --set-mark 1
iptables -A PREROUTING -t mangle -i eth0 -p tcp --dprot 80 -j MARK --set-mark 2

For the RDS table:

ip route add default via 10.1.1.1 dev eth1 table RDS	# the same like in the 
first example

For the ASTRAL table:

ip route add default via 10.8.8.1 dev eth2 table ASTRAL	# the same like in the 
first example

The next step is to have some routing rules based by the marked packets:

For the RDS:

ip rule add from all fwmark 1 table RDS

For the ASTRAL:

ip rule add from all fwmark 2 table ASTRAL

You can use the same commands to see the routing tables and rule lists as in the 
first example.
Now you have a routing solution based by the destination port...


```

---

