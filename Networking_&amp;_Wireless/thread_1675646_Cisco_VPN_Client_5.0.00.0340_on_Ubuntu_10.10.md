---
title: "Cisco VPN Client 5.0.00.0340 on Ubuntu 10.10?"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by ptyo on 2011-01-25
For some reason in order to connect to my work network we have to use the Cisco VPN Client 5.0.00.0340. I am brand new to Linux and have spent the better part of the day messing with VPN stuff trying to gain access to my work network. I came across the below website:

[http://www.nulldevice.de/2010/06/cisco-client-vpn-vpnc-ubuntu-linux-10-04/](http://www.nulldevice.de/2010/06/cisco-client-vpn-vpnc-ubuntu-linux-10-04/)

After following what they had to say, It says it connects and runs in the background, but I can't ping anything. Also I tried to use the network manager vpn setup. This shows  a little lock on my wireless making you think you are connected, but once agian you can't ping anything. I noticed that prior to starting the vpn when i run a ifconfig it only shows three items eth0.... but after i connect with network manager it shows one more... Tunnel address or something? Either way I can't ping anything.

Also when I am in Windows and use the vpn client after I enter my user / pass I get the welcome message ... Which in linux after entering my user / pass I don't receive anything.

---

### Post by ptyo on 2011-01-27
Here is what I get when i do the ifconfig and I have connected to the VPN I created in network manager. The tun0 get added.


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.24.240.60  P-t-P:172.24.240.60  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:102 (102.0 B)

What I am wondering is if I am connected but the routing information needs to be added. I know when I am in windows and I vpn into our network I am able to ping computers on the internal network 10.0.0.0.

---

### Post by ptyo on 2011-01-27
After some more research I found I command that displays the route table for linux. Here is what I get: This ofcourse is once I connect to the vpn I setup in Network Manager...  It shows the lock on the wireless and the routing table show our work networks... but I can't ping?

me@pete:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
somenumber     192.168.1.1     255.255.255.255 UGH       0 0          0 eth1
somenumber    0.0.0.0         255.255.255.0   U         0 0          0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
10.10.10.0      0.0.0.0         255.255.255.0   U         0 0          0 tun0
10.64.0.0       0.0.0.0         255.255.0.0     U         0 0          0 tun0
10.48.0.0       0.0.0.0         255.255.0.0     U         0 0          0 tun0
10.32.0.0       0.0.0.0         255.255.0.0     U         0 0          0 tun0
10.24.0.0       0.0.0.0         255.255.0.0     U         0 0          0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
10.40.0.0       0.0.0.0         255.255.0.0     U         0 0          0 tun0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 tun0

I removed the IP address to our boxes for security reasons... So here is what I got. The tunnel is established I guess since I can see our networks... 10.64.0.0 etcc... But I Still have the problem that I can't ping anything or terminal services etc...  Anybody got any ideas I am stuck now... Networking is not my cup of tea.. 

:lolflag:

---

### Post by ptyo on 2011-01-27
Okay fixed it.. After running the above route command on my Linux box i was curious to see what my windows box had to say. Well the windows box had default gateways and the linux did not...

SO a few things i had to actually do.. 

First change from:

Cisco-UDP   to Nat-Traversal always..
PUt a check mark in the disable deed peer detection..
Went to IPV4 settings and manual added the routes and selected the box ignore automatically detected routes....  :KS

With these changes i am able to VPN into our network and control the computers there.. sweet...

---

