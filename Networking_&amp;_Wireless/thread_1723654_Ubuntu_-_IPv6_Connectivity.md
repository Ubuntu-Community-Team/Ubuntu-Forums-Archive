---
title: "Ubuntu - IPv6 Connectivity"
date: 2011-04-07
forum: Networking &amp; Wireless
---

### Post by j.bunce on 2011-04-07
Hi,

I have been trying to experiment with IPv6 in Ubuntu, however I am running into a few problems trying to connect.

I'm using a Tunnel Broker service from HE.net. The tunnel is operational, and I can ping devices in the IPv6 Internet from my router:

```

Sending 5, 100-byte ICMP Echos to 2001:470:0:64::2, timeout is 2 seconds:
Packet sent with a source address of 2001:470:CAAE::1
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 200/200/200 ms

```

2001:470:CAAE::1 is the Wireless interface on my router.

ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:8b:00:97  
          inet addr:172.16.0.3  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: 2001:470:caae::2/48 Scope:Global
          inet6 addr: fe80::1e65:9dff:fe8b:97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7757619 (7.7 MB)  TX bytes:1612352 (1.6 MB)
          Interrupt:16 Memory:f9270000-f9270100 
```

I've added the IPv6 default gateway to the Wireless interface via the GUI.

ndisc6 reports:
```
ndisc6 2001:470:caae::1 wlan0
Soliciting 2001:470:caae::1 (2001:470:caae::1) on wlan0...
Timed out.
Timed out.
Timed out.
No response.

```

```
show ipv6 neighbors
```

Reveals nothing on the Cisco device. Is there something I'm missing on the client configuration?

Regards,

Jake

---

### Post by lemming465 on 2011-04-07
I'm confused about your topology; the first example looks like a Cisco IOS ping result, but the second one looks like a Linux result.  Is there a PC lurking somewhere?

With a delegated 2001:470:caae::/48 prefix, I'm assuming the wired uplink toward the internet is something like:
   cisco 2001:470:caae:0::1/64 --> he relay 2001:470:caae:0::2/64

If that's the case, you need to configure a different /64 subnet and address such as 2001:470:caae:1::3/64 on the wireless interface of your Cisco access point / wifi router, and then use that as the gateway from your PC.

Note that ICMPv6 neighbor discovery is scope link only; if 2001:470:caae:0::1 really is on the HE tunnel, you can only do neighbor discovery on it from the other end of the tunnel at HE.  You might be able to reach it via ping6, but not via ndisc6.
If you configure a different address on a different subnet under the same /48 prefix on the cisco's wireless interface, a PC attached to that access point should be able to do neighbor discovery against that.

Write back with more details about the OS versions, devices, and routes, and we might be able to understand better.  Particularly helpful on the linux side would be the output from *ip address show; ip -4 route show; ip -6 route show*.

---

### Post by j.bunce on 2011-04-07
The topology is an Ubuntu client connected to a Cisco router. The Cisco router has an IPv6 connection through an IPv4 GRE Tunnel.

I have a /48 routed down to me from HE.net.

The router is connected to HE via another /64 subnet.

2001:470:caae:0::1 is the inside IPv6 address of the Wireless interface on the Cisco router. Using that address as the source, I can ping hosts on the IPv6 Internet.

The issue is with connecting from the Linux client to the Cisco router.

Requested information:

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 3c:4a:92:4a:37:30 brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 1c:65:9d:8b:00:97 brd ff:ff:ff:ff:ff:ff
    inet 172.16.0.3/24 brd 172.16.0.255 scope global wlan0
    inet6 2001:470:caae::2/48 scope global 
       valid_lft forever preferred_lft forever
    inet6 fe80::1e65:9dff:fe8b:97/64 scope link 
       valid_lft forever preferred_lft forever

172.16.0.0/24 dev wlan0  proto kernel  scope link  src 172.16.0.3  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via 172.16.0.1 dev wlan0  proto static

2001:470:caae::/48 dev wlan0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 0
fe80::/64 dev wlan0  proto kernel  metric 256  mtu 1500 advmss 1440 hoplimit 0
default via 2001:470:caae::1 dev wlan0  proto static  metric 1024  mtu 1500 advmss 1440 hoplimit 0



```


Please let me know if you require any further information.

Regards,

Jake

---

### Post by j.bunce on 2011-04-07
Just to clarify: 2001:470:1F12:16:: /64 is the Cisco -> HE subnet.

2001:470:caae::/48 is the subnet that I am routed down.

---

### Post by lemming465 on 2011-04-18
Normally IPv6 subnets are configured at LAN / VLAN interfaces as /64's.  So while you may have a /48 prefix routed, it's probably best to configure interfaces as /64's.

Try making the ubuntu PC and Cisco router wireless interfaces have global unicast addresses 2001:470:caae:0::2/64 and 2001:470:caae::1/64 respectively, and see if that works any better.  Failing to use a /64 on the Cisco side is particularly likely to mess things up, I think.

Also, the Cisco box should have a link-local unicast address with prefix fe80::/64 similar to the ubuntu fe80::1e65:9dff:fe8b:97/64.  What happens if the ubuntu box tries:
   a)  ping6 -I wlan0 fe80::zzzz   (where zzzz is the Cisco host part)
   b)  ping6 -I wlan0 2001:470:caae::1
   c)  ping6 -I wlan0 2001:470:0:64::2

Failure of (a) would suggest that the Cisco wifi router doesn't have IPv6 fully turned on for the wifi interface.  
Success of (a) but failure of (b) would suggest that there is a problem with the Cisco address configuration.
Success of (a) and (b) but failure of (c) would suggest there is a routing configuration problem on the Cisco, either a route is missing, or the Hurricane Electric tunnel is down, or something.

---

### Post by nutznboltz on 2011-05-26
arp -a in IPv6ese is

ip -6 neigh

---

