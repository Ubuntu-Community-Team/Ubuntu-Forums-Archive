---
title: "Two NIC's no internet"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by jriesenw on 2009-11-23
Hey There,

This box has been running great on my LAN network, however when I tried to add an interface with a public IP from my ISP I ran into some issues. I can ping both IP's just fine internally and externally. But when I try to connect to the internet from the box or pull up apache from another machine i get nothing. Could this be a routing issue? Any help would be appreciated. 

Here is my /etc/network/interfaces contents.

# The loopback network interface
auto lo
iface lo inet loopback

# The LAN NIC
auto eth1
iface eth1 inet static
address 192.168.120.5
netmask 255.255.255.0
network 192.168.120.0
gateway 192.168.120.1
dns-nameservers 192.168.120.12

#The WAN NIC
auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.248
gateway xxx.xxx.xxx.xxx
dns-nameservers xxx.xxx.xxx.xxx, xx.xxx.xxx.xxx

---

### Post by jriesenw on 2009-11-23
Anything I can check that might help me to clear up this issue?

---

### Post by Iowan on 2009-11-23
Post results of **route -n**
What is at 192.168.120.1?

---

### Post by t0mppa on 2009-11-23
The problem is most likely a routing issue, where you have two NICs and with both of them having a gateway in configuration, thus two default gateways. This is a problem, because both routes can't be used on default, so the system uses one of them and totally ignores the other.

Call it an educated guess, you can run **ip route list** (or **route -n** for a different output format, since Iowan beat me to it) to verify whether I'm right or wrong. If that's the case, the easiest solution is to remove the gateway from the LAN NIC (eth1) configuration on the interfaces file. That way the LAN NIC won't even try to route packages outside any networks that you haven't manually defined.

If that works for you, great. If not or if you want a more specific solution, then just reply with more information.

---

### Post by jriesenw on 2009-11-23
Iowan thanks for responding. here is my routing table.

[B]Kernel IP routing table
Destination          Gateway                 Genmask                  Flags Metric            Ref    Use Iface[/B]
EXTERNAL_IP         0.0.0.0                     255.255.255.248           U           0                 0           0 eth0
192.168.120.0       0.0.0.0                      255.255.255.0               U           0                 0          0 eth1
169.254.0.0           0.0.0.0                      255.255.0.0                  U           1000           0          0 eth1
0.0.0.0                   192.168.120.1          0.0.0.0                         UG         100             0          0 eth1

Also here is my IFCONFIG:

eth0      Link encap:Ethernet  HWaddr 00:09:5b:1e:XX:XX  
          inet addr:EXTERNAL_IP  Bcast:EXTERNAL_BRD  Mask:255.255.255.248
          inet6 addr: fe80::209:5bff:fe1e:3f7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:358 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10226 (10.2 KB)  TX bytes:59650 (59.6 KB)
          Interrupt:21 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:0e:a6:f0:72:15  
          inet addr:192.168.120.5  Bcast:192.168.120.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fef0:7215/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:171053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13488971 (13.4 MB)  TX bytes:183138205 (183.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1661453 (1.6 MB)  TX bytes:1661453 (1.6 MB)

---

### Post by baban on 2009-11-23
From the routing table output, this line is inportant:

0.0.0.0 192.168.120.1 0.0.0.0 UG 100 0 0 eth1

That means, your PC is using 192.168.120.1 as a default gateway, so it's routing to your lan (192.168.X.X is private address not being used for connecting to the internet)

So you can delete the default route for eth1 in /etc/network/interfaces and then check for result.

Also I was wondering, do you have a static IP from your internet provider?

---

### Post by Iowan on 2009-11-23
> **t0mppa said:**
> ... since Iowan beat me to it...That doesn't happen often... ;)

I agree that it can probably go away as a gateway entry, but I'm still curious what is at 192.168.120.1 - is there another router with internet connection?

---

### Post by jriesenw on 2009-11-23
I have a block of public IP's provided by my ISP. I have one bound to the router 192.168.120.1 which is routing traffic for my LAN. And I am wanting to add another IP to eth0 temporarily until DNS propagates for a domain I am hosting on this machine. Once that is finished I will remove the LAN connection for security. 

I will try to remove that default route.

---

