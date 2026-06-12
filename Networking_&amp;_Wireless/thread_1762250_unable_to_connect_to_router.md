---
title: "unable to connect to router"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by LucidParody on 2011-05-19
Hello,

I'm running Ubuntu 10.04LTS 64bit. The desktop running it does not connect to my router or the internet. My mac laptop does. When I installed windows on this desktop, it too could connect. But after reinstalling ubuntu, I cannot. I tried upgrading to the latest ubuntu, but that just bricks my computer. Here is my ifconfig:

```
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1d:09:95:39:76  
          inet6 addr: fe80::21d:9ff:fe95:3976/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6084 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5329704 (5.3 MB)  TX bytes:647474 (647.4 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:87171 (87.1 KB)  TX bytes:87171 (87.1 KB)
```

My router is running dd-wrt. I've searched, but found no answers. Any help?

---

### Post by WthIteh on 2011-05-19
What is output
```
cat /etc/network/interfaces
```
?

Also try
```
/etc/init.d/networking restart
```

---

### Post by LucidParody on 2011-05-19
restarting networking did not fix the problem.

```

cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

Thanks.

---

### Post by WthIteh on 2011-05-19
First try
```
ifconfig eth0 up
```
and check that it could get IP now automatically?

If failed, then add
```

auto eth0
iface eth0 inet dhcp

```
to /etc/network/interfaces file and restart networking again.

---

### Post by LucidParody on 2011-05-19
Nothing :(

```

lucidbox:~$ ifconfig eth0 up
SIOCSIFFLAGS: Permission denied
lucidbox:~$ sudo ifconfig eth0 up
lucidbox:~$ sudo gedit /etc/network/interfaces 
lucidbox:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1d:09:95:39:76
Sending on   LPF/eth0/00:1d:09:95:39:76
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]
lucidbox:~$ 

```

Same results as when I run dhclient3 eth0, i think.

---

### Post by WthIteh on 2011-05-19
It seems that there is no DHCP server. Are you sure that there is a DHCP server?

You could also use a static IP address. For example if your network has 192.168.10.0/24 range then you could for example pick 192.168.10.20 and config your interface with
```

ip a a 192.168.10.20/24 dev eth0

```

---

### Post by LucidParody on 2011-05-19
Nope, that did not work -- I have also tried creating a static IP for the mac address from the router and then manually configuring the IP at the desktop.

I'm pretty sure there's a dhcp server -- how else is the mac and windows connecting? I'm looking at my mac prefs right now -- it's configuring using a dhcp server.

---

### Post by WthIteh on 2011-05-19
> **LucidParody said:**
> Nope, that did not work -- I have also tried creating a static IP for the mac address from the router and then manually configuring the IP at the desktop.

I'm pretty sure there's a dhcp server -- how else is the mac and windows connecting? I'm looking at my mac prefs right now -- it's configuring using a dhcp server.
OK, so check the IP address that "mac" acquires and then set it in "Linux" with "ip a a". Then try to ping router. Do not change your router settings while doing these tests.

---

### Post by LucidParody on 2011-05-19
Sorry, I should have been clearer in my original post.

(a) I tried your suggestion earlier.
(b) I've tried creating a static address from the router and manually configuring my desktop with ubuntu.
(c) A DHCP server exists; other computers in the household use it.

---

### Post by LucidParody on 2011-05-19
After following your steps, the networking icon is now missing from the panel...

---

### Post by WthIteh on 2011-05-20
The networking icon is for the NetworkManager applet and is not important.
You could always return to previous settings by running previous command and using "ip a d" instead of "ip a a" (which means "IP address delete" and "IP address add" respectively) and then logging-out/in. If you do not see the icon yet, you could right-click on the top panel and select "Add to panel" and select the applet again.

BTW, if you ran the "ip a a some-ip-address/24 dev eth0", now you must be able to see the Ip address in "ifconfig" output. If yes, paste the output of a ping command (pinging the router).
From do not change router settings, I mean: The same settings which allow MAC to connect should be used when you are testing with Ubuntu. If you do not configured manual IP address in router when MAC works, do not do so when testing Ubuntu too (completely same configuration).

---

### Post by LucidParody on 2011-05-20
```
lucidbox:~$ ping google.com
ping: unknown host google.com
lucidbox:~$ ip a a 192.168.1.116/149 dev eth0
Error: an inet prefix is expected rather than "192.168.1.116/149".
lucidbox:~$ ip a a 192.168.1.116 dev eth0
RTNETLINK answers: Operation not permitted
lucidbox:~$ sudo ip a a 192.168.1.116 dev eth0
lucidbox:~$ ifconfig eth0 up
SIOCSIFFLAGS: Permission denied
lucidbox:~$ sudo ifconfig eth0 up
lucidbox:~$ ping google.com
ping: unknown host google.com
lucidbox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:95:39:76  
          inet addr:192.168.1.116  Bcast:0.0.0.0  Mask:255.255.255.255
          inet6 addr: fe80::21d:9ff:fe95:3976/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:9214 (9.2 KB)  TX bytes:12198 (12.1 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9423 (9.4 KB)  TX bytes:9423 (9.4 KB)

lucidbox:~$ ping google.com
ping: unknown host google.com
lucidbox:~$ ping 192.168.1.1
connect: Network is unreachable

```

---

### Post by WthIteh on 2011-05-21
It's OK. Just instead of
```
sudo ip a a 192.168.1.116 dev eth0
```
use
```
sudo ip a a 192.168.1.116/24 dev eth0
```
command. So it knows about netmask (by /24).
Then you should be able to
```
ping 192.168.1.1
```

---

### Post by LucidParody on 2011-05-21
still no luck

```
lucidbox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:95:39:76  
          inet6 addr: fe80::21d:9ff:fe95:3976/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2004 (2.0 KB)  TX bytes:1152 (1.1 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8393 (8.3 KB)  TX bytes:8393 (8.3 KB)

lucidbox:~$ sudo ip a a 192.168.1.116/24 dev eth0
[sudo] password for tom: 
lucidbox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:95:39:76  
          inet addr:192.168.1.116  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe95:3976/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2368 (2.3 KB)  TX bytes:4085 (4.0 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8687 (8.6 KB)  TX bytes:8687 (8.6 KB)

lucidbox:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.116 icmp_seq=1 Destination Host Unreachable
From 192.168.1.116 icmp_seq=2 Destination Host Unreachable
From 192.168.1.116 icmp_seq=3 Destination Host Unreachable
From 192.168.1.116 icmp_seq=5 Destination Host Unreachable
From 192.168.1.116 icmp_seq=6 Destination Host Unreachable
From 192.168.1.116 icmp_seq=7 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
8 packets transmitted, 0 received, +6 errors, 100% packet loss, time 7004ms
, pipe 3
lucidbox:~$ ping google.com
ping: unknown host google.com

```

---

### Post by WthIteh on 2011-05-22
But it could send ping packets (it didn't) now to the router.
You could do two tests now:
1. Use
```
sudo ip a a 192.168.1.201/24 dev eth0
```
to be sure there is no problem due to ARP cache of router.
2. Run "Wireshark" or "tcpdump" to see is there any response packet/error or simply nothing.

---

### Post by LucidParody on 2011-05-22
```

eth0      Link encap:Ethernet  HWaddr 00:1d:09:95:39:76  
          inet6 addr: fe80::21d:9ff:fe95:3976/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6122 (6.1 KB)  TX bytes:1152 (1.1 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9312 (9.3 KB)  TX bytes:9312 (9.3 KB)

lucidbox:~$ sudo ip a a 192.168.1.201/24 dev eth0
[sudo] password for tom: 
lucidbox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:95:39:76  
          inet addr:192.168.1.201  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe95:3976/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:9209 (9.2 KB)  TX bytes:5351 (5.3 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9312 (9.3 KB)  TX bytes:9312 (9.3 KB)

lucidbox:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.201 icmp_seq=1 Destination Host Unreachable
From 192.168.1.201 icmp_seq=2 Destination Host Unreachable
From 192.168.1.201 icmp_seq=3 Destination Host Unreachable
From 192.168.1.201 icmp_seq=5 Destination Host Unreachable
From 192.168.1.201 icmp_seq=6 Destination Host Unreachable
From 192.168.1.201 icmp_seq=7 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6006ms
, pipe 3
lucidbox:~$ ping google.com
connect: Network is unreachable
lucidbox:~$ 


```

still nothing :(

---

### Post by dineshs on 2011-05-23
If you are using BT homehub please see postcount #11 and #12 [here]("http://ubuntuforums.org/showthread.php?t=1753698&page=2")
> After following your steps, the networking icon is now missing from the panel... 
Edit your /etc/network/interfaces as before(as in postcount #3) then restart
Note:You can configure DHCP/manual IP via Networkmanager.If you do it via /etc/network/interfaces NM will not manage your devices/the icon may disappear

---

