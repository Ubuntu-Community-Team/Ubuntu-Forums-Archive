---
title: "only local network no internet"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by webik on 2009-03-27
Hi

After update I've got problem with network on both LAN and WiFi connection is the same. 
I have interface up, i have IP address assigned using DHCP server. I can ping host in my local network but when I try ping other servers i.e. ubuntu.com there is a problem. I get information "Unknow host" - is the same when I use domain name and IP address. I checked this on 2 different routers and had same situation.

Thanks in advance.

webik

---

### Post by doas777 on 2009-03-27
ok, open a terminal and type:
```
ifconfig

```

and show us the output.

---

### Post by webik on 2009-03-27
Using LAN - interface eth0
```

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:17:08:38:2d:2f  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe38:2d2f/64 Scope:Link               
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1              
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0             
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0           
          collisions:0 txqueuelen:1000                                    
          RX bytes:13110 (13.1 KB)  TX bytes:5965 (5.9 KB)                
          Interrupt:16                                                    

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:25193 (25.1 KB)  TX bytes:25193 (25.1 KB)

vnet0     Link encap:Ethernet  HWaddr e6:33:f8:8f:6f:d3
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::e433:f8ff:fe8f:6fd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:4854 (4.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:f5:ab:36
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-F5-AB-36-00-00-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ping ubuntu.com
ping: unknown host ubuntu.com

ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=11.3 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.13 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=3.13 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=10.3 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.14 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=1.13 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1.25 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=1.38 ms
^C
--- 192.168.1.1 ping statistics ---
9 packets transmitted, 8 received, 11% packet loss, time 8045ms
rtt min/avg/max/mdev = 1.130/3.851/11.308/4.075 ms

```
Using wireless - interface wlan0
```

ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:17:08:38:2d:2f  
          inet6 addr: fe80::217:8ff:fe38:2d2f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1       
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16944 (16.9 KB)  TX bytes:5965 (5.9 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:30993 (30.9 KB)  TX bytes:30993 (30.9 KB)

vnet0     Link encap:Ethernet  HWaddr e6:33:f8:8f:6f:d3
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::e433:f8ff:fe8f:6fd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:5460 (5.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:f5:ab:36
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fef5:ab36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1606 (1.6 KB)  TX bytes:6065 (6.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-F5-AB-36-62-33-00-00-00-00-00-00-00-00
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ping ubuntu.com
ping: unknown host ubuntu.com

ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=11.3 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.13 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=3.13 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=10.3 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.14 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=1.13 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=1.25 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=1.38 ms
^C
--- 192.168.1.1 ping statistics ---
9 packets transmitted, 8 received, 11% packet loss, time 8045ms
rtt min/avg/max/mdev = 1.130/3.851/11.308/4.075 ms


```

192.168.1.1 - my router, i check also my router public IP and is reachable

BTW. Where I can find list of package that I upgraded?? I try to downgrade them.

webik

---

### Post by doas777 on 2009-03-27
ok, what is the output of :
```

cat /etc/resolv.conf
nslookup www.google.com

```
?

---

### Post by webik on 2009-03-27
```

cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

nslookup google.com
;; connection timed out; no servers could be reached

```

---

### Post by doas777 on 2009-03-27
ok, the line in your /etc/resolv.conf is the problem.
it thinks your PC is the DNS server, and my guess is that that is an error in judgement.

do you have another working Pc? if so, what OS does it have>

---

### Post by webik on 2009-03-27
hmm, I don't have  another working Pc. I'm using live CD to write this posts.

---

### Post by doas777 on 2009-03-27
thats fine,

whats the output of ```
sudo cat /etc/resolv.conf
```
when on the live CD?

we want to find out a legitimate DNS server address from it, so we can replace 127.0.0.1 in your resolv.conf file.

write down the DNS server address, and then reboot into your installed instance. 
```

gksu gedit /etc/resolv.conf 

```

and replace 'nameserver 127.0.0.1' with 'nameserver <the IP you wrote down>'

then save and close gedit.

```

sudo /etc/init.d/networking restart
nslookup www.google.com

```

the real problem here may be your DHCP server. make sure that it;s not passing 127.0.0.1 as the DNS server address.

---

### Post by webik on 2009-03-27
I try this, but I tred ping on two different routers and DHCP server - it was the same situation.

During last update dhcp client package is upgraded maybe there is problem.

---

### Post by webik on 2009-03-28
Hey it helps but I must do it every time when I connect to network using network manager.

I do a little research - stript that create reslov.conf "/sbin/dhclient-script" didn't executed.
 
I modify /etc/dhcp3/dhclient-exit-hooks.d/debug script and /etc/dhcp3/dhclient-enter-hooks.d/debug -> RUN = "yes", but no output debug file in /tmp is created during setting new connection. When I manualy run /sbin/dhclient-script output debug is created so debug script is ok.


I don't know that is the reason but it's wired for me.


Also in /etc/dhcp3/dhclient-exit-hooks.d/debug script I found: 

```

#All these scripts
# are called from /etc/dhcp3/dhclient-script, which exports all the
# variables shown before.

```

but the real location of dhclient-script is /sbin/dhclient-script - it should be only incrrect comment, but it colud be problem with moved script.

Anyone can help me with this. 

P.S doas777 thanks for your help :) Now I have temporary solution :)

---

