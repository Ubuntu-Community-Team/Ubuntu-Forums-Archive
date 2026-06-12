---
title: "Change or reconfigure network connection"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by ferrion on 2012-03-21
Hi guys,

when I right-click "Edit Connections">left click "ifupdown (eth0)", net manager has no response while "Wired connection 1" connection" will pop up a dialog box.

I wonder why I have 2 ethernet card(ipupdown(eth0) and wired connection 1)? As I have known, I have only a ethernet card.

I will try to find out:

1) Why this happened(2 ethernet card)&#65311;
2) How to change my default network connection to "wired connceton 1" or make when double clicking "ifupdown(eth0)" and it pop up a dialogbox to set DNS.

Any help will welcome. Thanks.

---

### Post by Ms. Daisy on 2012-03-22
Not sure if I'm understanding you.  The only thing that shows up in the network manager box is "wired connection 1", right?  That's probably eth0.

Open a terminal and type
```
ifconfig
```It will give you all your possible connections.  You should see something like this, which means that you have one NIC and one wired connection.  

```
eth0      Link encap:Ethernet  HWaddr 00:0f:fe:b3:f8:96  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:feb3:f896/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150778440 (150.7 MB)  TX bytes:15238748 (15.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:988 (988.0 B)  TX bytes:988 (988.0 B)
```

---

