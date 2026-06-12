---
title: "Lost domain name resolution"
date: 2012-11-07
forum: Networking &amp; Wireless
---

### Post by faroutliving on 2012-11-07
Sorry for what must be a brain dead question, but I'm tired and lost and could use a point in the right direction.

I have a very remote server that I need to upgrade to at least 12.04 to (hopefully) resolve a nasty bug. I managed to get it upgraded to 11.10, but now it won't resolve DNS. Traceroute shows It keeps asking on the second eth port :-(

/etc/network/interfaces (still) contains:

auto eth0
iface eth0 inet dhcp

I figure I could add dns-nameservers to it, but also figured that a more proper way is now recommended.

Maybe there is a FAQ or something I am missing?

Thanks, Deron

---

### Post by papibe on 2012-11-07
Hi

It looks like the loopback got deleted. Try this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
Then:
```
sudo service networking restart
```
Let us know how it goes.
Regards.

---

### Post by faroutliving on 2012-11-07
Thanks, but not the problem. I was just posting the relevant bits. The file is unmodified from before the upgrade and contains:

eth1 is the second ethernet port that has a small local device (raid card) that this computer acts as the router for so I can monitor the raid health remotely.


```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet static
	address 192.168.2.1
	netmask 255.255.255.0
	network 192.168.2.0
	broadcast 192.168.2.255
	gateway 192.168.2.1

```

---

### Post by papibe on 2012-11-07
Could you post the results of these commands?
```
ifconfig -a

route -n

nslookup ubuntu.com

dig google.com
```
Regards.

---

### Post by faroutliving on 2012-11-07
I'm happy to post them. Sadly, it confuses me further, since it appears that everything is working ok with name resolution. It is a fundamental routing problem instead. Thanks for clearing that up for me.

Ping 74.125.137.101
From 192.168.2.1 icmp_seq=1 Destination Host Unreachable

Which should not be using 192.168.2.xxx (since the raid card is not connected to anything else...)

Thanks for your help!

Deron


ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:1f:bc:02:bd:1e  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:bcff:fe02:bd1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5600221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2818218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8469555620 (8.4 GB)  TX bytes:186351607 (186.3 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:1f:bc:02:bd:1f  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:bcff:fe02:bd1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53639 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2394 (2.3 KB)  TX bytes:2253654 (2.2 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5807105 (5.8 MB)  TX bytes:5807105 (5.8 MB)

```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

nslookup ubuntu.com
```
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156

```

dig google.com
```
; <<>> DiG 9.7.3 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 22218
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		251	IN	A	74.125.137.101
google.com.		251	IN	A	74.125.137.102
google.com.		251	IN	A	74.125.137.113
google.com.		251	IN	A	74.125.137.138
google.com.		251	IN	A	74.125.137.139
google.com.		251	IN	A	74.125.137.100

;; AUTHORITY SECTION:
google.com.		318280	IN	NS	ns1.google.com.
google.com.		318280	IN	NS	ns4.google.com.
google.com.		318280	IN	NS	ns2.google.com.
google.com.		318280	IN	NS	ns3.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.		181081	IN	A	216.239.32.10
ns2.google.com.		181081	IN	A	216.239.34.10
ns3.google.com.		181081	IN	A	216.239.36.10
ns4.google.com.		181081	IN	A	216.239.38.10

;; Query time: 21 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Wed Nov  7 16:12:51 2012
;; MSG SIZE  rcvd: 260

```

---

### Post by faroutliving on 2012-11-07
Since I can't ping an ip address, but I can ping the next computer, then I presume something is wrong with the routing?

The iptables is the same, and if I open them wide open I still have the same problem.

So where do I start to track this down? What controls this?

Thanks,

Deron

---

### Post by papibe on 2012-11-07
Thanks.

I think this is your problem:
> **faroutliving said:**
> route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth1**
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

```
Your default route is pointing to the raid instead to the router/internet.

Remove the gateway from eth1, and add a custom route to the private network. It should looks something like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.2.1
    netmask 255.255.255.0
    network 192.168.2.0
    broadcast 192.168.2.255
    [B]up ip route add 192.168.2.0/24 via 192.168.2.1
    down ip route del 192.168.2.0/24 via 192.168.2.1[/B]

```
DHCP on the other interface should take care of the default route.

Let us know how it goes.
Regards.

---

### Post by faroutliving on 2012-11-07
Thanks so much! I just came back to write that I removed the eth1 entry and things started to work. I guess it was just luck that it worked before.

I need to go do some reading, because I have no idea what you wrote means!

Thanks again!

Deron

---

### Post by papibe on 2012-11-07
:D Great! Glad I could help.

Please mark this thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

### Post by faroutliving on 2012-11-10
Just a bump to let you know that I have not been able to test this yet (I have a narrow window each night when I can restart the server) but will in the next few days.

Thanks again!
Deron

---

