---
title: "How do I troubleshoot service networking start problems?"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by jeffsilverm on 2010-02-11
[FONT="Arial"]I am running Ubuntu desktop 9.10.  I am trying to troubleshoot why service networking won't start.  When I give the command

[FONT="Courier New"]sudo service networking start[/FONT]
the response is
[FONT="Courier New"]start: Job failed to start[/FONT]

I haven't a clue where to start troubleshooting.

Use [FONT="Courier New"]ifconfig [/FONT]and [FONT="Courier New"]route[/FONT], I am able to connect up to the internet and one of my internal networks.

My [FONT="Courier New"]/etc/network/interfaces file[/FONT] is[/FONT]
[FONT="Courier New"]auto lo
iface lo inet loopback

# silverman@cute-ubuntu-9:~$ ifconfig eth0
# eth0      Link encap:Ethernet  HWaddr 00:0c:29:6e:a5:87  
#           inet addr:172.24.74.8  Bcast:172.24.74.63  Mask:255.255.255.192
#           inet6 addr: fe80::20c:29ff:fe6e:a587/64 Scope:Link
#           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
# silverman@cute-ubuntu-9:~$ netstat -rn
# Kernel IP routing table
# Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
# 172.24.74.0     0.0.0.0         255.255.255.192 U         0 0          0 eth0
# 10.0.0.0        0.0.0.0         255.0.0.0       U         0 0          0 eth1
# 0.0.0.0         172.24.74.62    0.0.0.0         UG        0 0          0 eth0
# silverman@cute-ubuntu-9:~$ 

iface eth0 inet static
   address 172.24.74.8
   netmask 255.255.255.192
   gateway 172.24.74.62
# silverman@cute-ubuntu-9:/etc/network$ sudo ifconfig eth1 10.0.0.8
# silverman@cute-ubuntu-9:/etc/network$ ping -c 4 10.0.0.4
# PING 10.0.0.4 (10.0.0.4) 56(84) bytes of data.
# 64 bytes from 10.0.0.4: icmp_seq=1 ttl=255 time=10.3 ms
iface eth1
   address 10.0.0.8
   netmask 255.255.255.0

# When I tested this when configured by hand, 2010-02-11, it didn't work.  More testing is called for
iface eth2
   address 10.0.10.8
   netmask 255.255.255.0[/FONT]

Any suggestions on what to try next?

Thank you

---

