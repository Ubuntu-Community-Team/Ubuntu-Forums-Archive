---
title: "2nd interface doesn't work."
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by cagdix on 2011-12-01
Hello;

I have a new server. I configured my first interface (eth0) when installation time. It works perfectly.

But I need 2nd nic to connect to iSCSi network. For this; I use the fallowing command:

> ifconfig eth1 192.168.9.15 netmask 255.255.255.0 upThe interface has been configured. But I can't ping to other hosts from this interface.

> root@germany:/etc/network#ifconfig

eth0      Link encap:Ethernet  HWaddr 14:fe:b5:c9:e6:08  
          inet addr:192.168.10.160  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57827 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3627173 (3.6 MB)  TX bytes:84367626 (84.3 MB)
          Interrupt:36 Memory:f2000000-f2012800 

eth1      Link encap:Ethernet  HWaddr 14:fe:b5:c9:e6:0a  
          inet addr:192.168.9.15  Bcast:192.168.9.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1780 (1.7 KB)  TX bytes:511 (511.0 B)
          Interrupt:48 Memory:f4000000-f4012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7657 (7.6 KB)  TX bytes:7657 (7.6 KB)> root@germany:/etc/network# lspci | grep NetXtreme
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
01:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
02:00.1 Ethernet controller: Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20)> root@germany:/etc/network# ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes> root@germany:/etc/network# ping 192.168.9.9 -c 1
PING 192.168.9.9 (192.168.9.9) 56(84) bytes of data.
From 192.168.9.15 icmp_seq=1 Destination Host Unreachable

--- 192.168.9.9 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0msHow can I solve this problem ?

---

### Post by praseodym on 2011-12-01
Try to deactivate the auto-negotiation:

```
ethtool -s eth1 speed 1000 autoneg off
/etc/init.d/networking restart
```

---

### Post by jonobr on 2011-12-01
Hello there 

welcome to the forums,

It looks like the configuration of your interfaces is good, your subnetting looks correct, and the result of ifconfig also looks correct and both interfaces are configure and up.


I wonder however if ip forwarding to enable routing is one.
If you open a terminal and type
```

cat /proc/sys/net/ipv4/ip_forward
```

if you get back as a zero, that needs to be a 1

doing 

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
will change it instantly but you will need to set it permanently

---

### Post by cagdix on 2011-12-01
Hello;

I tried both way..

```
root@germany:/etc/network# ethtool -s eth1 speed 1000 autoneg off
Cannot set new settings: Invalid argument
  not setting speed
  not setting autoneg
``````
root@germany:/etc/network# cat /proc/sys/net/ipv4/ip_forward
0
root@germany:/etc/network# echo 1 > /proc/sys/net/ipv4/ip_forward 
root@germany:/etc/network# cat /proc/sys/net/ipv4/ip_forward
1
root@germany:/etc/network# ping -c 1 192.168.9.11
PING 192.168.9.11 (192.168.9.11) 56(84) bytes of data.
From 192.168.9.15 icmp_seq=1 Destination Host Unreachable

--- 192.168.9.11 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

root@germany:/etc/network# /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
 * Disconnecting iSCSI targets
   ...done.
 * Stopping iSCSI initiator service
   ...done.
 * Disconnecting iSCSI targets
   ...done.
 * Stopping iSCSI initiator service
   ...done.
 * Starting iSCSI initiator service iscsid
   ...done.
 * Setting up iSCSI targets
   ...done.
ssh stop/waiting
ssh start/running, process 3003
 * Setting up iSCSI targets
   ...done.
ssh stop/waiting
ssh start/running, process 3082
   ...done.
root@germany:/etc/network# ping -c 1 192.168.9.11
PING 192.168.9.11 (192.168.9.11) 56(84) bytes of data.
From 192.168.9.15 icmp_seq=1 Destination Host Unreachable

--- 192.168.9.11 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms
```

---

### Post by collisionystm on 2011-12-01
I always edit my config files directly and have never had a problem.

You do not need routing turned on unless you are using your server as a router.

```
sudo nano /etc/network/interfaces
```



> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.10.160
        netmask 255.255.225.0
        gateway xxx.xxx.xxx.xxx
        broadcast 192.168.10.255

auto eth1
iface eth1 inet static
        address 192.168.9.15
        netmask 255.255.255.0
        gateway xxx.xxx.xxx.xxx
        broadcast 192.168.9.255


save file

restart networking service one of 2 ways

sudo service networking restart

sudo /etc/init.d/networking restart

---

### Post by collisionystm on 2011-12-01
And the correct way to do ip forwarding

sudo nano /etc/sysctl.conf

uncomment this line

# Uncomment the next line to enable packet forwarding for IPv4
**#**net.ipv4.ip_forward=1

restart networking

Like I said. You only enable routing if your server is acting as a router / gateway

---

### Post by cagdix on 2011-12-02
I SOLVED THE PROBLEM!

Sorry for wasting your time. I solved the problem.

Please guess what the problem ?

No,
No,
No,

...
..

Oxidized switch port.. The green led is blinking, but not allow the transfer.. Just a 3Com...

Thank you again..

---

### Post by jonobr on 2011-12-02
I used to work for 3Com, Go easy :P
Glad you got to the bottom of it

---

