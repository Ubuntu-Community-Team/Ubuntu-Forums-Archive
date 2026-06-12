---
title: "Help! Hurricane Electric IPv6 no longer works after router upgrade."
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by yangjiangnan on 2012-07-11
Previously, I set up an IPv6 tunnel in Ubuntu 10.10 to Hurricane Electric and everything was working fine. However, a few days ago, my IPv6 stopped working. The most important thing I did was upgrading the firmware of my Netgear router (WNR2000v2). So I suppose it caused the problem, although I am not sure why. 

Now, I have tried to restore my system to a previous version (I copied "cp -a" most folders in / to backup, then delete the original folders and copy back after booting from live CD system, which successfully restored the system every time). I have also forward port 41 to my Ubuntu local IP, and allowed ping response in the router. My public IP address have not changed for a year. However, the IPv6 is still not working and I have no idea what is going wrong. 

I can ping6 my own ipv6 address but not ipv6.google.com. Any suggestions will be appreciated.
jiangnan@jiangnan-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:25:23:e5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:fe25:23e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91995 (91.9 KB)  TX bytes:63749 (63.7 KB)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9654 (9.6 KB)  TX bytes:9654 (9.6 KB)

sit0      Link encap:IPv6-in-IPv4  
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sit1      Link encap:IPv6-in-IPv4  
          inet6 addr: 2001:470:1f06:c0e::2/64 Scope:Global
          UP POINTOPOINT RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:7848 (7.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:8c:dd:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by lemming465 on 2012-07-14
Did the outside public IPv4 address from your ISP of your router change when it reloaded after the firmware upgrade?  That would break the tunnel.  Have you tried deleting the old tunnel and remaking a new one?

---

### Post by yangjiangnan on 2012-07-14
> **lemming465 said:**
> Did the outside public IPv4 address from your ISP of your router change when it reloaded after the firmware upgrade?  That would break the tunnel.  Have you tried deleting the old tunnel and remaking a new one?

My outside public IP address never changed. I remember my public IP and I use it everyday to connect back to home. Now I have re-created a tunnel and reset the commands, but it is still not working. Someone in HE forum said port 41 is not protocol 41. So, I am not sure if it is my router that is blocking IPv6 access.

---

### Post by Kirk Schnable on 2012-07-15
> **yangjiangnan said:**
> My outside public IP address never changed. I remember my public IP and I use it everyday to connect back to home. Now I have re-created a tunnel and reset the commands, but it is still not working. Someone in HE forum said port 41 is not protocol 41. So, I am not sure if it is my router that is blocking IPv6 access.

It's not IPv6 to your router. Hurricane Electric's IPv6 tunnel is tunneling IPv6 over IPv4, so even if your router has no support for IPv6, it doesn't matter, the tunnel should work. 

Kirk

---

### Post by lemming465 on 2012-07-16
The HE tunnel is a "6in4" style tunnel, meaning the IPv6 packets are carried as the data payload of an IPv4 packet.  As noted, the protocol type of such an encapsulated packet is 41, IP in IP; protocols 1,2,6,17 are ICMP, IGMP, TCP, UDP respectively.  Your router has to pass protocol 41 packets for the HE tunnel to work, yes.

---

### Post by hawkmage on 2012-07-16
What do you have in your /etc/network/interfaces file?   

Also what is the output from the commands:
```
ifconfig
route -n
route -nA inet6
```

---

### Post by yangjiangnan on 2012-07-16
> **hawkmage said:**
> What do you have in your /etc/network/interfaces file?   

Also what is the output from the commands:
```
ifconfig
route -n
route -nA inet6
```

jiangnan@jiangnan-PC:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
jiangnan@jiangnan-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:25:23:e5  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:fe25:23e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2930493 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4040137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:731153811 (731.1 MB)  TX bytes:3648001174 (3.6 GB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2048282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2048282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3592252623 (3.5 GB)  TX bytes:3592252623 (3.5 GB)

sit0      Link encap:IPv6-in-IPv4  
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sit1      Link encap:IPv6-in-IPv4  
          inet6 addr: 2001:470:1f06:4d4::2/64 Scope:Global
          UP POINTOPOINT RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:1975512 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:8c:dd:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

jiangnan@jiangnan-PC:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
jiangnan@jiangnan-PC:~$ route -nA inet6
Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
::/96                          ::                         Un   256 0     0 sit0
2001:470:1f06:4d4::/64         ::                         Un   256 0     0 sit1
fe80::/64                      ::                         U    256 0     0 eth0
fe80::/64                      ::                         Un   256 0     0 sit1
::/0                           ::                         U    1   0     0 sit1
::/0                           ::                         !n   -1  1 19552 lo
::1/128                        ::                         Un   0   1   821 lo
::127.0.0.1/128                ::                         Un   0   1     0 lo
2001:470:1f06:4d4::2/128       ::                         Un   0   1    69 lo
fe80::62eb:69ff:fe25:23e5/128  ::                         Un   0   1     0 lo
ff00::/8                       ::                         U    256 0     0 eth0
ff00::/8                       ::                         U    256 0     0 sit1
::/0                           ::                         !n   -1  1 19552 lo

---

### Post by yangjiangnan on 2012-07-17
> **lemming465 said:**
> The HE tunnel is a "6in4" style tunnel, meaning the IPv6 packets are carried as the data payload of an IPv4 packet.  As noted, the protocol type of such an encapsulated packet is 41, IP in IP; protocols 1,2,6,17 are ICMP, IGMP, TCP, UDP respectively.  Your router has to pass protocol 41 packets for the HE tunnel to work, yes.

Then do you think that Netgear is stupid enough to suddenly disable passing protocol 41? I see no reason for them to do that. Now I have made my tunnel box's internal IP the Default DMZ Server on the router setting.  This should enable passing protocol 41, right? However, IPv6 is still not working.

---

### Post by yangjiangnan on 2012-07-17
Whatever the reason is, now I have restored the firmware to a previous version downloaded from the official site ([http://downloadcenter.netgear.com/en/default.aspx](http://downloadcenter.netgear.com/en/default.aspx)), and everything starts working again. It seems that not everything newer is better. Netgear is stupid this time.

---

### Post by hawkmage on 2012-07-17
Your interfaces and routing look OK, did you set up the HE tunnel in the Network Manager?  I expected to see the tunnel interface defined in the interfaces file.

It is odd that a firmware revision would cause a rule to pass protocol 41 would stop working.  

Before my firewall supported IPv6 and IPv6 Tunnels I had a IPv6 Tunnel with HE functioning.  There are three things you need to make sure of to get the tunnel working: 

[LIST=1]
[*]The system with the tunnel defined can get to the HE Server IPv4 Address.
[*]The HE Tunnel Client IPv4 Address should be set to:
[LIST=1]
[*]If you are using NAT your Firewall/Router external IP address
[*] If you are using a internet routeable IPv4 address on the tunnel system then it should be the IPv4 address of the tunnel system.
[/LIST]
[*]Allow IP protocol 41 to the tunnel system.
[LIST=1]
[*] This would be part of you NAT rule if using NAT
[*]This would just be a rule allowing access to the internet routeable IP address for at least via protocol 41.
[/LIST]
[/LIST]
With an update to the router firmware items #1 and #2 should not be affected (really none of them should) but #3 is the likely place for the issue.

Did the new firmware on the router add support for an IPv6 Tunnel?  If so then it may be doing something with protocol 41 and ignoring your rule.  Also if your router supports the tunnel you may want to think about setting it up there so you have one location for configuring access in to and out of our network.

---

### Post by yangjiangnan on 2012-07-17
> **hawkmage said:**
> Your interfaces and routing look OK, did you set up the HE tunnel in the Network Manager?  I expected to see the tunnel interface defined in the interfaces file.

It is odd that a firmware revision would cause a rule to pass protocol 41 would stop working.  

Before my firewall supported IPv6 and IPv6 Tunnels I had a IPv6 Tunnel with HE functioning.  There are three things you need to make sure of to get the tunnel working: 

[LIST=1]
[*]The system with the tunnel defined can get to the HE Server IPv4 Address.
[*]The HE Tunnel Client IPv4 Address should be set to:
[LIST=1]
[*]If you are using NAT your Firewall/Router external IP address
[*] If you are using a internet routeable IPv4 address on the tunnel system then it should be the IPv4 address of the tunnel system.
[/LIST]
 
[*]Allow IP protocol 41 to the tunnel system.
[LIST=1]
[*] This would be part of you NAT rule if using NAT
[*]This would just be a rule allowing access to the internet routeable IP address for at least via protocol 41.
[/LIST]
 
[/LIST]
With an update to the router firmware items #1 and #2 should not be affected (really none of them should) but #3 is the likely place for the issue.

Did the new firmware on the router add support for an IPv6 Tunnel?  If so then it may be doing something with protocol 41 and ignoring your rule.  Also if your router supports the tunnel you may want to think about setting it up there so you have one location for configuring access in to and out of our network.

I set up HE tunnel just using the commands HE provided in their Example Configurations Linux-net-tools on their website.

You are right, the new firmware have added IPv6 supports. There were several options I for "**Internet Connection Type**" could choose in the new firmware:
Disabled
Auto Detect
6to4 tunnel
Pass Through
Fixed
DHCP
PPPoE
Auto Config
I am not very sure what all these options do, but I tried all of them (just using the default settings there), none of them helped passing protocol 41. So, I have no idea why they disabled protocol 41. I cannot find anything on the router setting page about protocol 41 configurations or about any other protocol configurations.

---

