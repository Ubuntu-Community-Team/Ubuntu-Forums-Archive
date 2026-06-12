---
title: "Ethernet AND wifi at the same time ?"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by naoli on 2009-01-31
Hello,

in order to perform some tests, I have access to **2 different internet access points**, one on my **ethernet** card and one on my **wifi** card (IP : 192.168.1.1 and 192.168.2.1, mask 255.255.255.0 for both).

**When I'm connected to any one, it works fine**.
But when I'm connected to **both** at the same time, nothing works and I can't access the web, although my ethernet card IP do is 192.168.2.x and my wifi card IP do is 192.168.1.x.

Here are what may help you help me :

When I'm connected with ethernet and it works :

> $ip route
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.20  metric 1
169.254.0.0/16 dev eth0  scope link  metric 1000
default via 192.168.2.1 dev eth0  proto static
$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

Then I get access to the wifi too :
> 
ip route
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.20  metric 1
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.20  metric 2
169.254.0.0/16 dev eth0  scope link  metric 1000
default via 192.168.2.1 dev eth0  proto static
$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

Ping on wifi works :
> 
$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=10.9 ms

Strange : ping on ethernet does not work except with sudo privileges :


> 
$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 192.168.2.1 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1000ms



$sudo ping 192.168.2.1
[sudo] password:
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=1.23 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=1.16 ms
^C
--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1004ms
rtt min/avg/max/mdev = 1.160/1.196/1.233/0.050 ms


Should any one have an idea, it would be wonderful ! :)

---

### Post by FishRCynic on 2009-01-31
(this probably won't work - shouldn't your wireless be wlan0 or similar)



try bridging them
[http://linuxcommand.org/man_pages/brctl8.html](http://linuxcommand.org/man_pages/brctl8.html)

install bridge utils
using commandline or synaptic 

the with something like this in terminal

brctl addbr br0 etho eth1

to make a bridge

stop networking and restart it

---

### Post by Shippou on 2009-01-31
I think these should not be activated at the same time.

This is also my problem, because I can't connect to the net when wireless and ethernet is on.

---

### Post by Iowan on 2009-01-31
Post results from **ifconfig -a** under both conditions.  Your **route** results suggest **avahi** may have assigned a 169.254.x.x address (which tends to cause issues with "normal" networks)

---

### Post by j0rd on 2009-02-26
Im having a similar issue after upgrading from 8.04 to 8.10...my net no longer works. Not wired, not wireless. I also get the ping error mentioned below.

$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

---

### Post by j0rd on 2009-02-26
problem fix for me was disabling ipmasq by running "/etc/init.d/ipmasq stop" as root.

Here's the thread where i found the answer:
[http://ubuntuforums.org/showthread.php?t=1041028&highlight=sendmsg%3A+operation+not+permitted](http://ubuntuforums.org/showthread.php?t=1041028&highlight=sendmsg%3A+operation+not+permitted)

---

