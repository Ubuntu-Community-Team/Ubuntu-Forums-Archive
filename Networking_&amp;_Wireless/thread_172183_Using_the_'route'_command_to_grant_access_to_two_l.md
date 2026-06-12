---
title: "Using the 'route' command to grant access to two local networks."
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by brushhead on 2006-05-08
Hi,
I am using Ubuntu as a file server.  I also am disting TV over ethernet, and for this I have got a Gigabit network.  The problem I have is that the TV traffic is multicast, and this will swamp my 10/100 VOIP adapter, and my WiFi access point.  I have therefore elected to separate my equipment into a dedicated TV network, and a separate 10/100 network for the non Gigabit LAN gear.

I want to be able to route non broadcast traffic between my two networks, for print serving and the like.  I was under the impression that I could simply use the 'route' command to give access between the two networks.  Is this correct?

I have the output from 'route' as follows.

robwilson@LNGBKER0001:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
robwilson@LNGBKER0001:~$


Ifconfig yeilds...

robwilson@LNGBKER0001:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:46:3A:BE:B9
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe3a:beb9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1012020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1488965709 (1.3 GiB)  TX bytes:7116 (6.9 KiB)
          Interrupt:16 Base address:0xa000

eth1      Link encap:Ethernet  HWaddr 00:06:4F:0D:74:B4
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:4fff:fe0d:74b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:374738 (365.9 KiB)  TX bytes:255753 (249.7 KiB)
          Interrupt:19 Base address:0xe800

Eth0 is the Gigabit adapter.  I have the router and firewall on the 10/100 side, ie on Eth1.

I would be grateful for any advice.

Regards,

Rob.

---

### Post by mips on 2006-05-08
is ipforwarding enabled ?

---

### Post by brushhead on 2006-05-08
According to /etc/network/options, yes it is.

---

### Post by mips on 2006-05-08
Do a search in the Howto section for 'router', there is a nifty guide by Ellias

---

### Post by Azrael on 2006-05-08
Your routing table seems fine as it is. If you have IP forwarding enabled (echo 1 > /proc/sys/net/ipv4/ip_forward) it should just work.

edit: All hosts other than LNGBKER0001 that want to send traffic to the other network must have LNGBKER0001 listed as a gateway, of course.

---

