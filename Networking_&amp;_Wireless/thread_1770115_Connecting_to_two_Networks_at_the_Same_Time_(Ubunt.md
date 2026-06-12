---
title: "Connecting to two Networks at the Same Time (Ubuntu 11.04)"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by DBQ on 2011-05-28
Hi Everybody.

I would like to my laptop to connect to two networks at the same time.

The first network is wireless through which I access the Internet.

The other network is a wired router to which my laptop and another computer are connected. I would like to connect to the two networks at the same time so I can access the Internet, and talk to the other computer on the wired lan.

My problem right now that I can only connect to one network at a time. Even the act of plugging in the cable for the wired network causes the wireless to cease functioning.  Any ideas?  I goggled but no help.  Could somebody give specific steps. I am on Ubuntu 11.04.

---

### Post by DBQ on 2011-05-28
P.S. Here is the output of my ifconfig where eth0 is the wired and wlan0 is the wireless.

eth0      Link encap:Ethernet  HWaddr 00:1c:25:98:82:b4  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe98:82b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1013173 (1.0 MB)  TX bytes:519374 (519.3 KB)
          Memory:fc200000-fc220000 


wlan0     Link encap:Ethernet  HWaddr 00:21:6b:3c:39:82  
          inet addr:192.168.2.92  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fe3c:3982/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13483461 (13.4 MB)  TX bytes:2953681 (2.9 MB)

---

### Post by Iowan on 2011-05-28
Well, both interfaces have IP addresses. Post the results of **route -n** with both interfaces active.

---

### Post by DBQ on 2011-05-28
Here it is:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by Iowan on 2011-05-28
> **DBQ said:**
> Here it is:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
[COLOR="Red"]0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0[/COLOR]Hmmm... the gateway is eth0 - internet traffic won't get to the internet.  You *might* be able to adjust the route settings via Network Manager.

---

### Post by DBQ on 2011-05-28
Which settings would I need to tweak? I basically need to set the default gateway to the wireless right? Which entries would I need to change?

---

### Post by Iowan on 2011-05-28
Be forewarned - I'm plowing unfamiliar territory here...

Network Manager>Auto eth0>Edit>IPv4 Settings>Routes has a checkbox to "Use this connection only for resources on its network" and another one marked "Ignore automatically obtained routes". One/either/both *might* disable the gateway on eth0. If the gateway stays on wlan0, you should be good... otherwise, you might need to manually add a gateway to the wlan0 setting. 

I remember a similar thread from a previous version - but haven't located it yet.

---

### Post by DBQ on 2011-05-29
I have configured the network manager the way you described and set the gateway manually to be on wlan0.

So now, I am able to use the internet and connect to the other network.  However, although I am able to ping another host on the wired router, I am not able to ssh to it.  Here are the new outputs

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:1c:25:98:82:b4  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe98:82b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:250786 (250.7 KB)  TX bytes:60282 (60.2 KB)
          Memory:fc200000-fc220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:521 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39517 (39.5 KB)  TX bytes:39517 (39.5 KB)

virbr0    Link encap:Ethernet  HWaddr 46:73:38:e0:5c:f2  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:14588 (14.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:3c:39:82  
          inet addr:192.168.2.92  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fe3c:3982/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1947957 (1.9 MB)  TX bytes:833116 (833.1 KB)


```

route -n

```

192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0




```

Also, I am able to ssh from the other computer on the router to the current one (for which the output is given above), but it works.  But not from current one to the other.  ssh itself is not the cause -- I tested it.

---

### Post by DBQ on 2011-05-29
I wonder if this is somehow related to the routing tables.

---

### Post by Iowan on 2011-05-29
> **DBQ said:**
>  ssh itself is not the cause -- I tested it.

Tested it - how?
Kinda sounds like the SSH server isn't set up on the other machine, but...

---

### Post by DBQ on 2011-05-29
On the target machine, I tried to ssh to self, and it worked. So I think the ssh server is fine.  However, when I try to do it from the other machine it does not work.

Is there some routing configuration that I need to check on the target machine?

---

### Post by Iowan on 2011-05-29
Sounds like a valid test of SSH.  I'm still a bit curious if the SSH configuration is OK. Out of curiosity, are you connecting  SSH (or trying to) via IP address or machine name?

---

### Post by DBQ on 2011-05-29
I use the IP

---

### Post by DBQ on 2011-05-29
Any ideas about what else I could try?

BTW, thank you so much for all your advice.

---

