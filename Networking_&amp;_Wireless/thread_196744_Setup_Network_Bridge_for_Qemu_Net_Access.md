---
title: "Setup Network Bridge for Qemu Net Access?"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by andb on 2006-06-14
I need a bit of advice installing qemu with networking. This exact procedure to make a bridge worked on a freinds machine, also dapper, right away. I am puzzled because I have no network access. Sorry if this is the wrong place to post, Im out of ideas... 

With only one app left in Windows, Im happy to be almost exclusively using Linux. This last one is a tough one though. Starcraft :)
I tried installing it under wine but it really hesitates a lot, if you switch between windows it hesitates terribly, even when the there are no other apps running. Further, I play over battlenet, so I must have network access in the virtual machine.

Ive found a HOWTO with TUN/TAP at [http://www.ubuntuforums.org/showthread.php?t=179472&highlight=qemu+network](http://www.ubuntuforums.org/showthread.php?t=179472&highlight=qemu+network) which seemed like overkill
and a nice simple way to use a bridge at [http://qemu.dad-answers.com/viewtopic.php?t=144](http://qemu.dad-answers.com/viewtopic.php?t=144)

So I've been trying this second way. 

My machine's default state is:
```
andrew@speedy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:DC:C6:CB:29
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fec6:cb29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2409416 (2.2 MiB)  TX bytes:852725 (832.7 KiB)
          Interrupt:193 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:49119 (47.9 KiB)  TX bytes:49119 (47.9 KiB)
```
I then enter the following commands:
```
ifdown eth0
ifconfig eth0 down
brctl addbr br0 
ifconfig eth0 up 
brctl addif br0 eth0 
ifconfig br0 up 
ifconfig br0 192.168.1.33
route add default gateway 192.168.1.22
```
The machine's configuration after is:
```
andrew@speedy:~$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:10:DC:C6:CB:29
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fec6:cb29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6220 (6.0 KiB)  TX bytes:3508 (3.4 KiB)

eth0      Link encap:Ethernet  HWaddr 00:10:DC:C6:CB:29
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fec6:cb29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6347 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2419123 (2.3 MiB)  TX bytes:855710 (835.6 KiB)
          Interrupt:193 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:49554 (48.3 KiB)  TX bytes:49554 (48.3 KiB)

andrew@speedy:~$ brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.0010dcc6cb29       no              eth0

andrew@speedy:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
default         192.168.1.22          0.0.0.0         UG    0      0        0 eth0
```
And here is my problem... No network activity...
```
andrew@speedy:~$ ping 192.168.1.22
PING 192.168.1.22 (192.168.1.22) 56(84) bytes of data.
From 192.168.1.101 icmp_seq=3 Destination Host Unreachable
From 192.168.1.101 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.22 ping statistics ---
6 packets transmitted, 0 received, +2 errors, 100% packet loss, time 5001ms
, pipe 2
```
To fix, I only have to remove eth0 from the bridge and re-add the default gateway, and all is ok.
 ```

andrew@speedy:~$ brctl delif br0 eth0 
andrew@speedy:~$ route add default gateway 192.168.1.22
```
I would greatly appreciate any advice to get this working... I have a feeling Im missing something simple. Once I get this sorted I'll have to make the definative starcraft HOWTO :)

---

### Post by djohnjimmy on 2006-08-15
I think your problem is ... you dont have NAT setup in your Dapper...

Try doing the following


this would setup the nat and then you can access network from your virtual machine...

CREATE A FILE "setup_nat" anywhere you want

then paste these lines into that file:::

-------------------------------------------------------------------------------------------------------------------------
 #!/bin/sh
sudo echo "1" > /proc/sys/net/ipv4/ip_forward

sudo /sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq

---------------------------------------------------------------------------------------------------------------------'
Change the permission of that file
chmod a+x ./setup_nat

then execute the file as the ROOT::

sudo ./setup_nat

This would setup the NAT on the host OS>..


Thats all you need to do...

Hope this helps..
John Jimmy Dondapati

---

### Post by andb on 2006-08-15
Thanks for the help, forgot about this post... Actually, I was specifically trying to avoid setting up NAT, wanting to use TUN/TAP to basically give the net card two IPs, one attached to UBUNTU, the other to the QEMU session. The NAT way is the most typical, but I like keeping my mahcine as simple as possible. The less there is to break, the less it will break is my policy. Finally got it working, but now I mostly use VMware, which set up exactly what I wanted out of the box. Thanks again!

---

