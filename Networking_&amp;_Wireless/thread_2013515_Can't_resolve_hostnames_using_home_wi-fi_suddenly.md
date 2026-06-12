---
title: "Can't resolve hostnames using home wi-fi suddenly"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by skaiuoquer on 2012-07-01
Came home from the office a couple of days ago with my work laptop, and I was suddenly unable to resolve domains. I was still able to connect to hosts directly through their IP addresses.

Other laptops connected to my home network both by wi-fi and LAN are able to do so normally.

Perhaps an important detail is that I use the ignominous Cisco AnyConnect client to connect to the VPN I use to work. I'm writting this post on my work laptop precisely because I'm able to connect to my VPN using the IP address of its server.

AnyConnect is an ugly beast, and may have caused all sorts of mayhem on my system's configuration without my knowledge. However, it is true that I was still able to connect normally at home for days after I originally installed AnyConnect. AnyConnect is able to update itself upon connection, so I can't discard it as a factor.

My laptop is running a fresh (week or two old) installation of Ubuntu 12.04 Precise, 64 bit. My router was using my ISP's DNS addresses, and I've since tried using OpenDNS, to no avail. I'm behind no proxy, as far as the configuration GUI can tell.

I have no idea which configuration files might be relevant, but will be gratefully willing to put them forth upon request. Any and all help is very, very welcome.

---

### Post by skaiuoquer on 2012-07-10
FYI - here's the contents of my /etc/network/interfaces file, as well as the outputs of ifconfig and iwconfig.

```

% cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

```

% ifconfig
cscotun0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.192.1.202  P-t-P:10.192.1.202  Mask:255.255.252.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1312  Metric:1
          RX packets:17150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:5560335 (5.5 MB)  TX bytes:20083419 (20.0 MB)

eth0      Link encap:Ethernet  HWaddr f0:4d:a2:90:4c:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 

eth1      Link encap:Ethernet  HWaddr 78:e4:00:37:98:4d  
          inet addr:10.20.6.110  Bcast:10.20.7.255  Mask:255.255.254.0
          inet6 addr: fe80::7ae4:ff:fe37:984d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1406  Metric:1
          RX packets:58941 errors:0 dropped:0 overruns:0 frame:537190
          TX packets:56382 errors:1769 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54829287 (54.8 MB)  TX bytes:29501651 (29.5 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:612609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:612609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78377604 (78.3 MB)  TX bytes:78377604 (78.3 MB)

```

```

%iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:180  Noise level:171
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

cscotun0  no wireless extensions.

```

Thanks.

---

