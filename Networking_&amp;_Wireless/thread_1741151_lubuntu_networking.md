---
title: "lubuntu networking"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by karma7 on 2011-04-27
hi, ive recently installed lubuntu 10.04 on an old sony vaio. ive been able to connect to the internet (satellite broadband) for a few months then no connection. the connection is fine so its definatly the network on the vaio. ive tried pinging to no avail. would love some advice 

thanks

---

### Post by slooksterpsv on 2011-04-27
Click on the LXDE Menu go to Accessories -> LXTerminal

Type in the following and press the enter key where it says <enter>:
```

ifconfig <enter>
ping 74.125.224.81 <enter>

```

On the ping 8.8.4.4 wait about 5 seconds then press CTRL+C to stop the pings. If you could get us the information from the terminal such as:

inet address
ping replies (if any, just one or two should suffice)

If you could reply that information that would be great.

EDIT: Also if you go through any routers or if its a direct connection. If you go through a router, restart the router (unplug the power cord, plug it back in and try it).

---

### Post by karma7 on 2011-04-27
hi n thanks for the response. 
when pinging after typing if config in terminal, no response at all 
when pinging just with root th response is
connect: network is unreachable

i dont go through router and network is working on my other laptop just not th vaio

cheers

---

### Post by cipherboy_loc on 2011-04-27
What are you using for a network manager? NetworkManger, WICD, or something else?

Cipherboy

---

### Post by slooksterpsv on 2011-04-28
ifconfig is one word, not 2; you may need to try: /sbin/ifconfig in the terminal you should get output like this:

```

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:87:8e:39  
          inet addr:192.168.0.81  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe87:8e39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:475305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:337635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:557439270 (557.4 MB)  TX bytes:42690413 (42.6 MB)

```

---

### Post by karma7 on 2011-05-01
thanks for your input the problem was with network manager and is now sorted.

cheers
karma7

---

