---
title: "unique issue?"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by adduds on 2011-02-28
This happens every couple boots:

I'll log into my computer ubuntu 10.10 shows i'm connected to (lifeportal ssid of my network) go into firefox and any other method (ie. ping google) and nothing not connecting

to get my wireless working I have to right click my wireless icon and uncheck enable wireless networking?? re-enable it then it works its annoying this happen to anything??

---

### Post by Iowan on 2011-02-28
When (un)connected, does **ifconfig -a** show valid IP address, and **route -n** show proper route/gateway? (does it change if/when wireless is dis/re-enabled?)

---

### Post by adduds on 2011-04-08
i'm still getting the problem this is my route and ifconfig prior to fixing the problem

```
toews@kidlapp:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
toews@kidlapp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:19:81:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13111 (13.1 KB)  TX bytes:13111 (13.1 KB)

wlan0     Link encap:Ethernet  HWaddr 5c:ac:4c:77:03:49  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5eac:4cff:fe77:349/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6522 (6.5 KB)  TX bytes:16329 (16.3 KB)

```

this is my route and ifconfig post fixing

```
toews@kidlapp:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
toews@kidlapp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:19:81:f8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20359 (20.3 KB)  TX bytes:20359 (20.3 KB)

wlan0     Link encap:Ethernet  HWaddr 5c:ac:4c:77:03:49  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5eac:4cff:fe77:349/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35460 (35.4 KB)  TX bytes:41175 (41.1 KB)

```

it connects but i have no internet connection I've just gotta do guess work on sudo ifconfig wlan0 down and disconnecting from the network aswell as disabling wireless and networking all randomly and eventually it works; my parents have the same issue with their laptop running ubuntu..... it shows a connected symbol ie. i'm on my network but no connection to the internet

---

### Post by adduds on 2011-04-09
bump

---

### Post by adduds on 2011-04-11
bump tryin' to keep this afloat here

---

### Post by Iowan on 2011-04-11
Perplexing...
A couple more things to check:
Can you **ping** the gateway (192.168.0.1) when disconnected?
Is this supposed to be a DHCP or static-addressed system?  

Check **man dhclient**  - in particular, information on the **-r** flag. I'm wondering if the client may be using an expired lease which gets released (somehow) when wireless is disabled...

---

### Post by adduds on 2011-04-11
> **Iowan said:**
> Perplexing...
A couple more things to check:
Can you **ping** the gateway (192.168.0.1) when disconnected?
Is this supposed to be a DHCP or static-addressed system?  

Check **man dhclient**  - in particular, information on the **-r** flag. I'm wondering if the client may be using an expired lease which gets released (somehow) when wireless is disabled...

my eth0 line is static; wlan0 is DHCP

the other laptop on the network is DHCP

ok thank you next time the issue occurs i'll try those

---

