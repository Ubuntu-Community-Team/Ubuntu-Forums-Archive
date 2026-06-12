---
title: "VPN Connection Sharing via tap0 not tracking connections"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by rsinger104 on 2010-08-30
There is no “free” VPN client for MAC that will work with the VPN Gateway I’m connecting to.  What I’m trying to do is connect via Ubuntu, a vmware Guest OS, to the VPN Gateway and share that connection with the host OS (OSX 10.5.8).  The host OS will only be routed to subnets behind the VPN gateway via the Ubuntu VPN connection.

I’ve already read through many articles and forum posts on this subject, such as:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
[http://communities.vmware.com/thread/120047](http://communities.vmware.com/thread/120047)
[http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/)
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)
…and a few others


Here’s my current config:

```
OSX 10.5.8
VMWare Fusion 3.1
Ubuntu 
Shrew Soft VPN Client for Ubuntu

192.168.1.0/24 LAN Subnet
172.16.2.0/24 Private VMWare Subnet

192.168.1.1 LAN Router
192.168.1.107 Ubuntu LAN (eth0)
192.168.1.106 OSX LAN

172.16.2.1 OSX Private VMWare Intfc
172.16.2.131 Ubuntu Private VMWare Intfc (eth1)

2.1.1.1 VPN Gateway
1.1.1.1 Ubuntu tunnel intfc (tap0)
1.2.1.0 Subnet Behind VPN
```


So let me start by explaining what does work:

I can successfully establish a VPN connection from the Ubuntu box to the remote Gateway and all functionality within the Ubuntu Guest OS seems to work as expected, with a couple of exceptions.

1.	ICMP/HTTP/FTP/DNS from (1.1.1.1) Ubuntu Guest OS to (1.2.1.0) Subnet Behind VPN
2.	ICMP from (1.1.1.1 or 192.168.107) Ubuntu Guest OS to (2.1.1.1) VPN Gateway

Basically everything from the Ubuntu box works as expected, except for the fact that I cannot ping from eth1 (172.16.2.131) nor eth0 (192.168.1.107) to anything on the VPN network.  Which makes me think that it’s an issue with the iptables forwarding rule.

Here is the rule on Ubuntu Guest OS that I have setup:
```
iptables -A FORWARD -i eth1 -o tap0 -s 172.16.2.0/24 -m conntrack --ctstate NEW -j ACCEPT

iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

iptables -A POSTROUTING -o tap0 -t nat -j MASQUERADE
```

Basically that should nat any outgoing packet from the tap0 interface after the routing has taken place and replace the IP with the tap0 IP.  And the strange part is that it DOES!!!  At least for ICMP.  The tcpdump on the Ubuntu eth1 interface shows the packets coming in from 172.16.2.1 and being routed for the 1.2.1.x subnet.  Interestingly, the tcpdump of eth0 even shows ICMP REPLIES!!!  The problem is that the destination address for those replies is the IP of the tap0 interface (of course) and the iptables never routes it any further.  This is what makes me think there’s an issue with conntrack of some kind.  But I’m not sure how to identify what it might be.

Also, I did verify that conntrack is on and so is ip_forwarding in the kernel and in sysctl.

Here is the config and info from the Ubuntu Guest OS box.  It’s all that really matters, because a ping from the private vmware interface on the ubuntu box fails in the same way.  If I can get that fixed, I’m sure the rest will work.

```
root@ubuntu:~# netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
2.1.1.1		 192.168.1.1     255.255.255.255 UGH       0 0          0 eth0
172.16.2.0      0.0.0.0         255.255.255.0   U         0 0          0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         1.1.1.1	  0.0.0.0         UG        0 0          0 tap0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0


root@ubuntu:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:29:a3:88:2c  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fea3:882c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:365 errors:365 dropped:0 overruns:0 frame:0
          TX packets:221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34056 (34.0 KB)  TX bytes:23990 (23.9 KB)
          Interrupt:19 Base address:0x2024 

eth1      Link encap:Ethernet  HWaddr 00:0c:29:a3:88:36  
          inet addr:172.16.2.131  Bcast:172.16.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fea3:8836/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:43 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4668 (4.6 KB)  TX bytes:5114 (5.1 KB)
          Interrupt:19 Base address:0x20a4 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1936 (1.9 KB)  TX bytes:1936 (1.9 KB)

tap0      Link encap:Ethernet  HWaddr de:f2:f5:9b:62:98  
          inet addr:1.1.1.1  Bcast:1.1.1.1  Mask:255.255.255.255
   UP BROADCAST RUNNING  MTU:1380  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@ubuntu:~# iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  172.16.2.0/24        0.0.0.0/0           ctstate NEW 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           ctstate RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

root@ubuntu:~# iptables -L -n -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


Would greatly appreciate any guidance or even “shot in the dark” ideas. &#9786;

---

### Post by rsinger104 on 2010-08-31
Any ideas what might be going on?

I've tried nat'ing the various  interfaces to see if anything changes, but no matter what interface I  nat, it seems like the conntrack doesn't work.  Because the reply comes  in, but isn't forwarded to the original interface.

---

