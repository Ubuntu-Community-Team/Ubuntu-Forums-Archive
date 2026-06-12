---
title: "Browsing problem HELP!!!!"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by shivugh on 2010-02-08
I Use Ubuntu linux 8.10 and from the last three days I am having trouble browsing the internet. It shows that I am connected to the internet / router but when I tried to browse using firefox or Ephipany, the page don't load, it's just remains white blank. Surprisingly when I tried browsing in windows xp, it works without any problem. 

I tried loads of things recommended in various forums like changing network.dns.disableipv6 to true and setting dns nameserver in etc/resolve.conf but it still doesn't work. 

This is really driving me crazy, it's been three days I got hooked to solving this problem but to no success.](*,) Please help!! :(

---

### Post by adam22030 on 2010-02-08
What happens if you try to ping another machine outside your network?

Adam

---

### Post by Iowan on 2010-02-08
Can you ping internet by IP address (74.125.95.105)?
Wired or wireless connection?
Does (from a terminal) **route -n** show your router for the default gateway (the line with "UG")?

---

### Post by Cabs21 on 2010-02-08
1) Are you wired or wireless connection?
2) If wireless then check your card Drivers and settings
3) If wired (which I suspect) your router is behind some sort or firewall that will not let you out of the local network.  You should be able to see other computers on your local network but not leave to connect to the world.  This is the issue I have at work.  Wired my laptop says connected but the signal is not leaving the building, wireless I get the internet.  The wired connection runs through some big white box (that I have no idea what it is) before it gets to the verizon router.

Have not tried this yet but give it a try and let me know what happens.

in windows run the command prompt.  START>RUN>cmd

type in 

```
ipconfig
```

look to see what your 
Connection-specific DNS Suffix is.

then boot to Ubuntu and enter that DNS suffix in your Ethernet connections settings.  That might just get you outside your network.

---

### Post by shivugh on 2010-02-08
Hi Guys,

When I ping 91.189.94.249 from the terminal

I get this output:

PING 91.189.94.249 (91.189.94.249) 56(84) bytes of data.
From 192.168.182.37 icmp_seq=2 Destination Host Unreachable
From 192.168.182.37 icmp_seq=3 Destination Host Unreachable

And ping ubuntu.com or google.com

returned :-

ping: unknown host ubuntu.com

But surprisingly after few seconds using ping -c 4 [www.google.com](www.google.com) and ping -c 2 91.189.94.249

returned :-

PING [www.l.google.com](www.l.google.com) (209.85.129.106) 56(84) bytes of data.
64 bytes from 209.85.129.106: icmp_seq=1 ttl=56 time=37.3 ms
64 bytes from 209.85.129.106: icmp_seq=2 ttl=56 time=35.9 ms
64 bytes from 209.85.129.106: icmp_seq=3 ttl=56 time=39.5 ms
64 bytes from 209.85.129.106: icmp_seq=4 ttl=56 time=38.9 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 15299ms
rtt min/avg/max/mdev = 35.969/37.953/39.542/1.409 ms

PING 91.189.94.249 (91.189.94.249) 56(84) bytes of data.
From 91.189.88.10 icmp_seq=1 Destination Host Unreachable
From 91.189.88.10 icmp_seq=2 Destination Host Unreachable

--- 91.189.94.249 ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 999ms
, pipe 2

I thought wow now it's started working again, so I browsed for 3 seconds then boom it's gone again. So I tried repeating ping -c 4 [www.google.com](www.google.com) or 91.189.94.249 for the second time but didn't yeild anything except - ping: unknown host [www.google.com](www.google.com) (or 91.189.94.249)

I could browse the internet for the first few seconds on rebooting ubuntu linux and then it's gone.

**@Cabs21 and Iowan **

I have wireless connection. 'Connection-specific DNS Suffix' is BLANK.

*Does (from a terminal) route -n show your router for the default gateway (the line with "UG")?*

Okay lemme try that. I need to switch back to ubuntu linux now and try the command. Will get back to you.

---

### Post by shivugh on 2010-02-08
:~$ route -n


Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

172.20.208.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0

192.168.182.0   0.0.0.0         255.255.255.0   U     2      0        0 eth1

169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

0.0.0.0         192.168.182.1   0.0.0.0         UG    0      0        0 eth1

0.0.0.0         172.20.208.254  0.0.0.0         UG    100    0        0 eth0

------------------------

*Few seconds later:-*

------------------------

:~$ route -n

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

192.168.182.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1

169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0

0.0.0.0         192.168.182.1   0.0.0.0         UG    0      0        0 eth1

0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

---

### Post by shivugh on 2010-02-08
I tried to ping the ip, Broadcast addr., subnet mask and the default gateway. Here's what I got:-

:~$ ping -c 2 192.168.182.37
PING 192.168.182.37 (192.168.182.37) 56(84) bytes of data.
64 bytes from 192.168.182.37: icmp_seq=1 ttl=64 time=0.085 ms
64 bytes from 192.168.182.37: icmp_seq=2 ttl=64 time=0.086 ms

--- 192.168.182.37 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.085/0.085/0.086/0.009 ms

ping -b 192.168.182.255
WARNING: pinging broadcast address
PING 192.168.182.255 (192.168.182.255) 56(84) bytes of data.
64 bytes from 192.168.182.1: icmp_seq=1 ttl=64 time=4.65 ms
.
.
.


:~$ ping -c 2 255.255.255.0
PING 255.255.255.0 (255.255.255.0) 56(84) bytes of data.

--- 255.255.255.0 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1012ms


:~$ ping -c 4 192.168.182.1
PING 192.168.182.1 (192.168.182.1) 56(84) bytes of data.
64 bytes from 192.168.182.1: icmp_seq=1 ttl=64 time=8.32 ms
64 bytes from 192.168.182.1: icmp_seq=2 ttl=64 time=13.6 ms
64 bytes from 192.168.182.1: icmp_seq=3 ttl=64 time=12.1 ms
64 bytes from 192.168.182.1: icmp_seq=4 ttl=64 time=7.45 ms

--- 192.168.182.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3012ms
rtt min/avg/max/mdev = 7.450/10.389/13.606/2.570 ms

:~$ ping -c 4 192.168.182.1
PING 192.168.182.1 (192.168.182.1) 56(84) bytes of data.
64 bytes from 192.168.182.1: icmp_seq=1 ttl=64 time=7.68 ms
64 bytes from 192.168.182.1: icmp_seq=2 ttl=64 time=4.95 ms

--- 192.168.182.1 ping statistics ---
4 packets transmitted, 2 received, 50% packet loss, time 3006ms
rtt min/avg/max/mdev = 4.953/6.318/7.684/1.367 ms

:~$ ping -c 4 192.168.182.1
PING 192.168.182.1 (192.168.182.1) 56(84) bytes of data.
64 bytes from 192.168.182.1: icmp_seq=4 ttl=64 time=4545 ms

--- 192.168.182.1 ping statistics ---
4 packets transmitted, 1 received, 75% packet loss, time 3012ms
rtt min/avg/max/mdev = 4545.386/4545.386/4545.386/0.000 ms

---

### Post by Temppu on 2010-02-08
I am having exactly the same problem. Can ping in home network, not outside.

Internet works fine, as I am writing this on my netbook in the same network, using the same wireless.

---

### Post by Temppu on 2010-02-08
> **Temppu said:**
> I am having exactly the same problem. Can ping in home network, not outside.

Internet works fine, as I am writing this on my netbook in the same network, using the same wireless.

And this problem is only there when using wireless.

---

### Post by Iowan on 2010-02-08
> **shivugh said:**
> :~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.182.1   0.0.0.0         UG    0      0        0 eth1
0.0.0.0         172.20.208.254  0.0.0.0         UG    100    0        0 eth0

*Few seconds later:-*
:~$ route -n

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.182.1   0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
Which way works? The first one shows two default gateways (which should confuse the machine). It's also showing two active interfaces. Do you have both wired and wireless connected? What happens if wired is disconnected?

---

### Post by shivugh on 2010-02-08
@ Iowan

Thanks for responding mate. I don't have a wired connection but I happened to use it before switching to wireless about four days ago. 192.168.xxx.x is the wireless gateway address. I got this one from running /etc/network/interfaces :-

auto lo
iface lo inet loopback

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp



iface eth0 inet static
address 172.xx.xxx.xx
netmask 255.255.255.0
gateway 172.20.xxx.xxx

auto eth0

I am not an expert on ubuntu linux, so could you please suggest me how I could solve this internet problem? :???:

---

### Post by Iowan on 2010-02-08
I'm not an expert either... 
If you're willing, try commenting out everything in */etc/network/interfaces* **except** the (first) two lines that define "lo". Restart or reboot (I usually reboot to get NM and networking re-synched). Unless it's evolved, Intrepid's NM was a li'l touchy. If this doesn't work, we can try enabling **only** the wireless interface (eth1?).

---

### Post by shivugh on 2010-02-09
auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet static
address 172.20.xxx.xx
netmask 255.255.255.0
gateway 172.20.xxx.xxx


auto eth0

---

### Post by shivugh on 2010-02-09
eth1 is for wireless interface

---

