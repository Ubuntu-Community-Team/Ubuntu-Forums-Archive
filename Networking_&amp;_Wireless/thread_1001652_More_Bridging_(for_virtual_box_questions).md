---
title: "More Bridging (for virtual box questions)"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by supremedalek on 2008-12-04
Ok, I feel like I still am Homer Simpson regarding bridging. And, yes, the reason I am interested on it right now is because of VirtualBox. In any case, I tried to create a bridge using the virtualbox programs (after getting the package), which means I am using vbox0 instead of tap0:

```
raub@monaco:~$ sudo VBoxTunctl -t vbox0 -u raub
Set 'vbox0' persistent and owned by uid 1000
raub@monaco:~$ ls -l /dev/vboxdrv
crw-rw---- 1 root vboxusers 10, 63 2008-12-02 22:06 /dev/vboxdrv
raub@monaco:~$  sudo VBoxAddIF vbox0 raub br0
VirtualBox host networking interface creation utility, version 2.0.6
(C) 2005-2007 Sun Microsystems, Inc.
All rights reserved.

Creating the permanent host networking interface "vbox0" for user raub.
raub@monaco:~$ 
raub@monaco:~$ tail /etc/group
[...]
vboxusers:x:125:raub
raub@monaco:~$ 
raub@monaco:~$ cat /etc/network/interfaces
# Loopback
auto lo
iface lo inet loopback

# Bridging setup for virtual box
auto br0
iface br0 inet dhcp
    bridge_ports eth0
raub@monaco:~$

```

I restarted networking, saw that my dhcpd gave both br0 and eth0 the ip 10.0.0.115. Then I decided to see if I can see someone:

```
raub@monaco:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 br0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 eth0
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 br0
raub@monaco:~$ ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
From 10.0.0.115 icmp_seq=2 Destination Host Unreachable
From 10.0.0.115 icmp_seq=3 Destination Host Unreachable
From 10.0.0.115 icmp_seq=5 Destination Host Unreachable
From 10.0.0.115 icmp_seq=6 Destination Host Unreachable

--- 10.0.0.1 ping statistics ---
9 packets transmitted, 0 received, +4 errors, 100% packet loss, time 8024ms
, pipe 2
raub@monaco:~$ ping 10.0.0.115
PING 10.0.0.115 (10.0.0.115) 56(84) bytes of data.
64 bytes from 10.0.0.115: icmp_seq=1 ttl=64 time=0.057 ms
64 bytes from 10.0.0.115: icmp_seq=2 ttl=64 time=0.050 ms
64 bytes from 10.0.0.115: icmp_seq=3 ttl=64 time=0.051 ms

--- 10.0.0.115 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.050/0.052/0.057/0.008 ms
raub@monaco:~$

```

Anything I could be missing here?

---

### Post by zeefreak on 2009-10-11
i seem to be having the same problem. it is really odd.

config: 
   host: winxp
   guest: ubuntu server 9.04

when i have virtualbox set up as nat, i can ping my router, but cannot ping anything on the lan, and nothing can ping it, though i am able to browse the web. when i change it to bridged, i get a valid ip from the router, but then i can't ping anything, including the router, and i am not able to browse the web.

in a nutshell, how is it that i'm being given an ip from the router, and then i can't ever connect to the router again? i just don't understand how that works . . .

---

