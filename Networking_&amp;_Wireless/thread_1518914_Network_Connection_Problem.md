---
title: "Network Connection Problem"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by ario on 2010-06-27
Can not ping the other computer from my Ubuntu PC.
When I boot my PC with Ubuntu 10.04 live CD it can connect to other computer via a cross-over LAN cable. But when it boots from installed Ubuntu 10.04 on its hard-drive, It can not ping the other computer and connection fails.
I have two Ethernet Cards installed on my PC. I also have installed VirtualBox (Maybe the problem is by that).
This is the response of route -n command:
```
root@ario-desktop:/home/ario# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
89.165.81.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
```

This is the file /etc/network/interfaces:
```
auto lo
iface lo inet loopback


iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
```
I believe that the problem is with configurations. Because with the exact hardware, Operating system and IP addresses I can ping both ways on Live CD but can not do it on Installed one.
Any helps will be appreciated.

---

### Post by dineshs on 2010-06-28
No default gateway?
I get this for route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
117.196.144.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         117.196.144.1   0.0.0.0         UG    0      0        0 ppp0

and /etc/network/interfaces contains only this
 
```
auto lo
iface lo inet loopback
```
I configure DSL via NM like this
[http://ubuntuforums.org/showpost.php?p=9516979&postcount=3](http://ubuntuforums.org/showpost.php?p=9516979&postcount=3)

---

### Post by ario on 2010-06-30
Let me solve it myself!
Well obviously I have two Ethernet cards. One is used for connecting to Laptop (My Via LAN Card), The other one is always connected to the DSL modem (My RealTek On board LAN). And this is the main problem.
LAN Connection to laptop from desktop sometimes can be done by RealTek Item in network manager, and sometimes by the Via one. [B]It seems that network manager applet which shows two Ethernet options to connect trough (For me RealTek and Via) can not decide which one is exactly for which Ethernet card. It just show me two different names, But sometimes the real Ethernet card that is connected is named Via, and Sometimes it is named RealTek in network manager menu.
The second problem is that the [/B]*pon*** command sometimes tries to connect trough the first Ethernet Card, and sometimes trough the second one.** So I decided to do this routine and suggest anyone who has the same problem to do the same on UBUNTU 10.04:
You must:
1. Turn off the DSL modem so that you make sure no other connected device is active.
2. Try to connect to your laptop trough Via Item.
3. If not try to connect to your laptop trough RealTek Item.
4. When succeed in connecting your laptop, Turn on DSL modem and try to connect to Internet by other ethernet Item.
5. Make sure that none of Network Connections in Network Manager is set to "Connect Automatically".
So I solved the ugly "Operation not permitted" error and...
Good wishes!

---

