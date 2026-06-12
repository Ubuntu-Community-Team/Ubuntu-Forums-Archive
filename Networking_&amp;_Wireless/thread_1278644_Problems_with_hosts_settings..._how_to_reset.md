---
title: "Problems with hosts settings... how to reset?"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by esauer on 2009-09-29
I am running ubuntu server 8.04. I recently moved apartments and since then, I can't run anything that involves resolving hostnames (i.e. wget, apt-get install, apt-get update, etc.). However, I am able to ssh into the box, also apache is still working and i can access it via the web. I am assuming there are messed up host settings since I moved apartments/switched ISPs. I found an entry for my old ISP in /etc/hosts, but I don't remember ever needing to add that manually in order to connect to the network. Can someone help me reset my connection/host settings so that it will automatically connect? 

I am using a wired connection to a linksys router and have a static ip set.

Thanks!

---

### Post by chili555 on 2009-09-29
This must be DNS day!!

Please post the output of:```
cat /etc/resolv.conf
route -n
```Thanks.

---

### Post by esauer on 2009-09-29
So i guess from the output below, I can see that, despite deleting the entry for comcast in my hosts file, its still trying to connect to it.

```
:~$ cat /etc/resolv.conf
search hsd1.il.comcast.net.
nameserver 68.87.72.130
nameserver 68.87.77.130

:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0


```

---

### Post by chili555 on 2009-09-29
> despite deleting the entry for comcast in my hostsI assume Comcast is your old ISP? Let's see if we can whip a kwik fix on it. Please do:```
sudo gedit /etc/resolv.conf
```Use your favorite text editor if you don't have gedit. Remove ***all*** the old wordings and add this:```
nameserver 192.168.1.1
```Proofread, save and close. Now do:```
ping -c3 www.google.com
```If Google is resolved into an IP address and you get ping returns, you should be all set.

I don't think any reference to Comcast, or any other ISP, should exist in */etc/hosts*. Can we please have a peek at:```
cat /etc/hosts
```Thanks.

---

### Post by esauer on 2009-09-29
Looks like it worked... though I don't think I normally see packet loss when pinging...

```

:~$ ping -c3 www.google.com
PING www.l.google.com (64.233.169.104) 56(84) bytes of data.
64 bytes from 64.233.169.104: icmp_seq=1 ttl=243 time=639 ms
64 bytes from 64.233.169.104: icmp_seq=3 ttl=243 time=649 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 11651ms
rtt min/avg/max/mdev = 639.067/644.199/649.331/5.132 ms

```

also my hosts file:
```

:~$ cat /etc/hosts
127.0.0.1       localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by chili555 on 2009-09-29
> I can't run anything that involves resolving hostnames (i.e. wget, apt-get install, apt-get update, etc.)Is your original problem fixed? The ping time seems quite long, as well. May we please see:```
ifconfig eth0
sudo ethtool eth0
```Your */etc/hosts* looks just fine.

---

### Post by esauer on 2009-09-29
Yes, original problem is solved.... but it HAS been taking a really long time. I have been running apt-get update for about 20 minutes. Also response time in my ssh session has been extremely slow.

Here is the output you asked for:

```
:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:30:18:bf:ae:14
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:febf:ae14/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:653618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:48340527 (48.3 MB)  TX bytes:40249028 (40.2 MB)
          Interrupt:11 Base address:0xa000

:~$ sudo ethtool eth0
[sudo] password for esauer:
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

```

---

### Post by esauer on 2009-09-30
Also, I am getting average download times of about 9 kbps

---

### Post by chili555 on 2009-09-30
Your *ifconfig* and *ethtool* numbers look entirely normal to me; no errors and no collisions. Are there other computers connected to the router that have acceptable speeds? Have you checked with your internet service provider? 

You could also log in to the router to chech which DNS nameservers are being used and substitute them in */etc/resolv.conf* to see if that makes any difference. I think that's doubtful; I have four computers with both setups and all speeds are similar, that is, fast. My ping times to Google, with the router's IP address as the nameserver, are around 21 ms.

Is there any change if you do:```
sudo ifconfig eth0 mtu 1492
```Thanks.

---

### Post by esauer on 2009-09-30
I think it must be my ISP right now. I just checked my other machines and they are the same. I'll give them a call later today. Thanks for your help with everything else!

---

### Post by chili555 on 2009-09-30
> I think it must be my ISP right nowTell them chili555 concurs! Happy to be of help.

---

