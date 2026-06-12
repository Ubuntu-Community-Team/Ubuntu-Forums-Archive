---
title: "cannot temporarily change MTU"
date: 2012-05-21
forum: Networking &amp; Wireless
---

### Post by jfbooth on 2012-05-21
This is version 12.04.  Trying to test a new MTU setting.  Machine is connected via ETH (0) cable to Cisco WIFI router connected to cable modem.

```
jb@Compaq-PC:~$ ping -s 36888 -c1 google.com
PING google.com (74.125.227.99) 36888(36916) bytes of data.
36896 bytes from dfw06s16-in-f3.1e100.net (74.125.227.99): icmp_req=1 ttl=57 time=86.4 ms

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 86.461/86.461/86.461/0.000 ms

jb@Compaq-PC:~$ sudo ifconfig mtu 36916
[sudo] password for jb: 
[COLOR="Red"]SIOCSIFADDR: No such device
mtu: ERROR while getting interface flags: No such device[/COLOR]
```

As you can see I deduced 36916 as a 'tolerable' value, but when I try to set MTU (temporarily) I get the red error.

Here are the current MTU, etc. settings:

```
jb@Compaq-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:d1:3c:1f:10  
          inet addr:192.168.1.133  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd22:eb95:5916:0:7526:bdf3:e885:a9a1/64 Scope:Global
          inet6 addr: fd22:eb95:5916:0:214:d1ff:fe3c:1f10/64 Scope:Global
          inet6 addr: fe80::214:d1ff:fe3c:1f10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20193868 (20.1 MB)  TX bytes:8740142 (8.7 MB)
          Interrupt:3 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1028261 (1.0 MB)  TX bytes:1028261 (1.0 MB
```)

Any help is apreciated in advance.

---

### Post by papibe on 2012-05-21
> **jfbooth said:**
> 
jb@Compaq-PC:~$ sudo ifconfig mtu 36916

Hi jfbooth.

You are missing the name of interface (eth0 in this case).

Try this:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 mtu 1024
sudo ifconfig eth0 up
```
Hope it helps,
Regards.

---

### Post by jfbooth on 2012-05-21
> **papibe said:**
> You are missing the name of interface (eth0 in this case).

Try this:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 mtu 1024
sudo ifconfig eth0 up
```
Hope it helps,
Regards.

Thank you so much for the quick reply.  I was following instructions from another site .. literally.  They never mentioned any command other than what I mentioned.  Thank you again.  I have not yet tried your suggestion .. not at that computer,... but certainly will.  One thing .. doesn't an MTU of 36916 seem awfully high?  That website said to go as high as you can until it errors .. then use the one just less than that .. and 36916 was the 'break point' ... but it sure seems high to me.

I will mark this thread as solved .. once I get these puzzlements cleared up.  Thank you again.

---

