---
title: "Can't connect to internet"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by azuru on 2010-12-20
I am running Ubuntu 9.10 and after both of my gateways went out last week I haven't been able to connect to the internet form the box. I can ping locally to other computers on the network (there are about 60 between the two gateways) and I can ping to both gateways, but nothing past that. Also, I cannot ssh into the box despite allowing it in iptables. I have included some relevant information below:

```
sudo iptables --list --verbose
Chain INPUT (policy ACCEPT 418M packets, 26G bytes)
 pkts bytes target     prot opt in     out     source               destination
  908 36320 DROP       tcp  --  any    any     anywhere             anywhere            00 flags:RST/RST
    0     0 ACCEPT     tcp  --  any    any     localhost            anywhere
    0     0 DROP       tcp  --  any    any     anywhere             anywhere
12119  769K ACCEPT     tcp  --  any    any     anywhere             anywhere
28071 2400K ACCEPT     tcp  --  any    any     anywhere             anywhere
    8  1879 ACCEPT     tcp  --  any    any     anywhere             anywhere
53726 7462K ACCEPT     tcp  --  any    any     anywhere             anywhere            00
    0     0 ACCEPT     all  --  any    any     anywhere             75-151-117-137-Washiusiness.net state ESTABLISHED
14296 4596K DROP       all  --  any    any     anywhere             75-151-117-137-Washiusiness.net state NEW

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 100M packets, 1152G bytes)
 pkts bytes target     prot opt in     out     source               destination
```


```
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
75.151.117.136  *               255.255.255.252 U     0      0        0 eth4
10.0.1.0        *               255.255.255.0   U     0      0        0 eth2
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
localnet        *               255.255.255.0   U     0      0        0 eth3
link-local      *               255.255.0.0     U     1000   0        0 eth2
default         75-151-117-138- 0.0.0.0         UG    100    0        0 eth4
default         [www.uwsae.org](www.uwsae.org)   0.0.0.0         UG    100    0        0 eth3
default         10.0.1.1        0.0.0.0         UG    100    0        0 eth2
```


```
ifconfig
eth2      Link encap:Ethernet  HWaddr 00:e0:81:b8:e3:ab
          inet addr:10.0.1.10  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:feb8:e3ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84022206 errors:9 dropped:0 overruns:0 frame:9
          TX packets:66376937 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14902724459 (14.9 GB)  TX bytes:117435996677 (117.4 GB)
          Interrupt:27 Base address:0x8000

eth3      Link encap:Ethernet  HWaddr 00:e0:81:b8:e3:aa
          inet addr:10.18.56.10  Bcast:10.18.56.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:feb8:e3aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:411444386 errors:7 dropped:0 overruns:0 frame:7
          TX packets:89993436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:31689471822 (31.6 GB)  TX bytes:1193727164585 (1.1 TB)
          Interrupt:28 Base address:0xe000

eth4      Link encap:Ethernet  HWaddr 00:14:d1:1a:dc:dc
          inet addr:75.151.117.137  Bcast:75.151.117.139  Mask:255.255.255.252
          inet6 addr: fe80::214:d1ff:fe1a:dcdc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1280465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:155994298 (155.9 MB)  TX bytes:20707338 (20.7 MB)
          Interrupt:19 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:369879 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:45607276 (45.6 MB)  TX bytes:45607276 (45.6 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:17350563 (17.3 MB)
```

```
sudo cat /sudo cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet static
        address 10.0.1.10
        netmask 255.255.255.0
        network 10.0.1.0
        broadcast 10.0.1.255
        gateway 10.0.1.1
        # dns-* options are implemented by the resolvconf package, if installed
#       dns-nameservers 10.18.56.1

auto eth3
iface eth3 inet static
        address 10.18.56.10
        netmask 255.255.255.0
        network 10.18.56.0
        broadcast 10.18.56.255
        gateway 10.18.56.1
        # dns-* options are implemented by the resolvconf package, if installed

auto eth4
iface eth4 inet static
        address 75.151.117.137
        netmask 255.255.255.252
        network 75.151.117.136
        broadcast 75.151.117.139
        gateway 75.151.117.138
```

Also when i reset the network I get some errors, but i couldn't find anything in logs that seemed to be relevant.

 ```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                  RTNETLINK answers: No such process
RTNETLINK answers: No such process
                                                                                 [ OK ]
```

any thoughts?

---

### Post by azuru on 2010-12-20
It should also be noted that Eth4 is  the interface that all world-facing traffic uses, e.g. browsing and web server/ssh'ing in. Eth2 and Eth3 are internal ones, and eth0 and eth1 are no longer in use (I used to have a different mobo with onboard NICs, and when I upgraded ubuntu 'remembered' them and assumed that because now I had two *new* nics that they should be 2 and 3)

---

### Post by azuru on 2010-12-28
So after a little more investigation I found that Comcast had changed the true static settings on my gateway. I had them reset these to how I want them and now I can ssh in remotely, but I can still not ping out to anything.

---

### Post by Iowan on 2010-12-29
Does /*etc/resolv.conf * show the proper nameservers?
(Can you ping outside by IP address?)

---

### Post by drdos2006 on 2010-12-29
I had the same problem with my ISP changing some upstream settings. My resolution was to disable any IPv6 settings.

regards

---

### Post by azuru on 2010-12-29
> **Iowan said:**
> Does /*etc/resolv.conf * show the proper nameservers?
(Can you ping outside by IP address?)

I looked over the resolv.conf and everything looks fine.

when I ping I get

```

ping google.com
PING google.com (72.14.213.103) 56(84) bytes of data.
^C
--- google.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4008ms

```
so it would appear that the lookup is working just fine as the proper ip is being returned.

---

### Post by Iowan on 2010-12-30
I doubt it's the culprit, but another common villain is [MTU]("http://ubuntuforums.org/showthread.php?t=872346").

---

### Post by azuru on 2010-12-30
> **drdos2006 said:**
> I had the same problem with my ISP changing some upstream settings. My resolution was to disable any IPv6 settings.

regards

My aliases file was gone so I put all the IPV6 changes into a new .conf file and then restarted. I am now able to ping out, but I can't remotely ssh into the server anymore.

---

