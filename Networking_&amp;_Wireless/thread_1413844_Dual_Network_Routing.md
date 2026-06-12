---
title: "Dual Network Routing?"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by cuddles71 on 2010-02-22
Evening all. Quick networking question for you.

I have a server with 2 NICs. eth0 is direct connected to the internet, and eth1 is connected to my LAN's router.

What I'd like to do is make sure (almost) all traffic for the server goes through eth0, with just CUPS and Samba going through eth1.

When I run ifconfig, I get this:
```

eth0      Link encap:Ethernet  HWaddr 00:11:09:9f:60:6c  
          inet addr:192.168.254.5  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe9f:606c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:37 txqueuelen:1000 
          RX bytes:9199885 (9.1 MB)  TX bytes:10575986 (10.5 MB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:00:e8:12:96:c7  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe12:96c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1465971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:646889225 (646.8 MB)  TX bytes:1614017922 (1.6 GB)
          Interrupt:18 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:684166 (684.1 KB)  TX bytes:684166 (684.1 KB)

```

And route gives me:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
192.168.254.0   *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.254.254 0.0.0.0         UG    0      0        0 eth0

```

The reason I'm thinking that it's not working the way I'd like is that if I unhook the cable from eth1, ALL traffic on the server stops.

Attached is a simple diagram explaining the setup I'd like.

Thanks!

---

### Post by DGortze380 on 2010-02-23
> **cuddles71 said:**
> Evening all. Quick networking question for you.

I have a server with 2 NICs. eth0 is direct connected to the internet, and eth1 is connected to my LAN's router.

What I'd like to do is make sure (almost) all traffic for the server goes through eth0, with just CUPS and Samba going through eth1.

When I run ifconfig, I get this:
```

eth0      Link encap:Ethernet  HWaddr 00:11:09:9f:60:6c  
          inet addr:192.168.254.5  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe9f:606c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:37 txqueuelen:1000 
          RX bytes:9199885 (9.1 MB)  TX bytes:10575986 (10.5 MB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:00:e8:12:96:c7  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe12:96c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1465971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:646889225 (646.8 MB)  TX bytes:1614017922 (1.6 GB)
          Interrupt:18 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:684166 (684.1 KB)  TX bytes:684166 (684.1 KB)

```

And route gives me:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
192.168.254.0   *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.254.254 0.0.0.0         UG    0      0        0 eth0

```

The reason I'm thinking that it's not working the way I'd like is that if I unhook the cable from eth1, ALL traffic on the server stops.

Attached is a simple diagram explaining the setup I'd like.

Thanks!

This is typically handled with static routes and an IPTABLES PREROUTING chain.

--but--

If possible, the simplest way may be to bind Samba and CUPS to the IP on eth1 through their individual configurations. I have no experience with Samba or CUPS, so I'm not sure if this is possible in their configs.

---

### Post by cuddles71 on 2010-02-23
Can you point me to an example ofiptable prerouting? So far all I can find is for firewalling, which isn't what I want.

---

### Post by cuddles71 on 2010-02-24
bump.

---

### Post by Skaperen on 2010-02-24
Is this CUPS and Samba running on this server, used by others in the LAN ... or does this server need to access CUPS and Samba on other servers in the LAN?

What is the IP address range of all computers in the LAN?  192.168.0.1 through 192.168.0.254?  Any hosts in the LAN with other addresses may be getting to this server the wrong way.

If you are wanting other TYPES of traffic from hosts on the LAN to reach the server by eth0 instead of eth1, then they will need to be accessing the server via a different IP address ... or else you'll have to add port-based routing policies around your LAN's connections (e.g. expensive complex stuff).

Can the server ping to 192.168.254.254 when you unplug eth1?

What is NET2?  Another path to the internet?

---

### Post by cuddles71 on 2010-02-24
> **Skaperen said:**
> Is this CUPS and Samba running on this server, used by others in the LAN ... or does this server need to access CUPS and Samba on other servers in the LAN?

What is the IP address range of all computers in the LAN?  192.168.0.1 through 192.168.0.254?  Any hosts in the LAN with other addresses may be getting to this server the wrong way.

If you are wanting other TYPES of traffic from hosts on the LAN to reach the server by eth0 instead of eth1, then they will need to be accessing the server via a different IP address ... or else you'll have to add port-based routing policies around your LAN's connections (e.g. expensive complex stuff).

Can the server ping to 192.168.254.254 when you unplug eth1?

What is NET2?  Another path to the internet?

Samba are running on this server, and is accessed by the LAN computers. CUPS is running, but is used to access a networked printer.

The LAN IP range is 192.168.0.1 - 192.168.0.254

The server CAN ping 192.168.254.254 (the Net 1 connection) when eth1 is unplugged, but all other traffic stops dead (pinging yahoo.com for instance).

The problem is, this server is also a shoutcast server. And all the traffic from that is going over eth1 instead of eth0, which it should do by default. According to the Shoutcast forum folks, it's a problem in my routing tables.

Net 2 is the lan's connection to the internet. The server has it's own dedicated line on Net 1.

---

### Post by Skaperen on 2010-02-24
Where is your caching DNS server running?  E.g. what is the contents of your /etc/resolv.conf file.  For example mine has this contents:```
nameserver 172.30.0.4
nameserver 172.30.0.5
nameserver 172.30.0.6
```

Yours needs to NOT have any IP addresses that would be routed via eth1.  Is this server in question running DNS on its own?  Are there other hosts in the 192.168.254/24 subnet?

---

### Post by Skaperen on 2010-02-24
So you have 2 connections to the internet.  Do you have 2 different blocks of public IP space, one for each?  If yes, then you should be using the IP addresses for Net1 for services (like your shoutcast) that need to be handled by that server over its dedicated connection.  If I were to do a DNS lookup of your shoutcast service, what IP address would I get?  If I traced it from somewhere out on the internet, would it come in over Net1 or Net2?  If you would be willing to give an actual hostname, I could do an actual traceroute.

I believe they are right, it is a routing issue.  But just what, I can't say, yet, until I have a complete picture of everything on your network.

---

### Post by cuddles71 on 2010-02-24
> **Skaperen said:**
> Where is your caching DNS server running?  E.g. what is the contents of your /etc/resolv.conf file.  For example mine has this contents:```
nameserver 172.30.0.4
nameserver 172.30.0.5
nameserver 172.30.0.6
```

Yours needs to NOT have any IP addresses that would be routed via eth1.  Is this server in question running DNS on its own?  Are there other hosts in the 192.168.254/24 subnet?

I think you may have found the problem. :)

/etc/resolv.conf was pointing at 192.168.0.1, the firewall for the LAN and Net2

The DNS and nameserver for 192.168.254/24 is 192.168.254.254 (the router for Net1)

So I'm assuming I change that line to 192.168.254.254?

The hostname is kjsr.ath.cx if that helps.

---

### Post by Skaperen on 2010-02-24
If 192.168.254.254 is running DNS, use that.  Actually, it is OK to use DNS over on 192.168.0.0/24 as long as you don't mind of DNS queries done through that server will go out through the Net2 side.  But if you definitely want all DNS queries going out through (and replies coming back in through) Net1, then 192.168.254.0/24 is where the DNS needs to be.  It is possible to configure one machine to be DNS on both sides.

I traced kjsr.ath.cx (67.140.171.156) and the last hop was 151.213.31.169.  Tracing could be blocked at that point.  Is that the proper internet connection for the Net1 side?

Info that would help includes IP addresses of the links for both internet connections, as well as the IP address range being routed by the ISP(s) over those connections.  Then verify that public access hostnames have IP addresses corresponding to the correct connection coming in (or both in cases where you want some limited redundancy).

You may want to run a DNS resolver (bind9) on the server itself and put 127.0.0.1 in as the first nameserver entry in the /etc/resolv.conf file, and 192.168.254.254 as the second one.

---

### Post by cuddles71 on 2010-02-24
> **Skaperen said:**
> If 192.168.254.254 is running DNS, use that.  Actually, it is OK to use DNS over on 192.168.0.0/24 as long as you don't mind of DNS queries done through that server will go out through the Net2 side.  But if you definitely want all DNS queries going out through (and replies coming back in through) Net1, then 192.168.254.0/24 is where the DNS needs to be.  It is possible to configure one machine to be DNS on both sides.

I traced kjsr.ath.cx (67.140.171.156) and the last hop was 151.213.31.169.  Tracing could be blocked at that point.  Is that the proper internet connection for the Net1 side?

Info that would help includes IP addresses of the links for both internet connections, as well as the IP address range being routed by the ISP(s) over those connections.  Then verify that public access hostnames have IP addresses corresponding to the correct connection coming in (or both in cases where you want some limited redundancy).

You may want to run a DNS resolver (bind9) on the server itself and put 127.0.0.1 in as the first nameserver entry in the /etc/resolv.conf file, and 192.168.254.254 as the second one.

That's the right IP. 

I've installed bind9, and have changed the resolv.conf. Do I need to configure bind9 in any way?

---

