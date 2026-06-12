---
title: "Ubuntu 10.10 &amp; MAC adress"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by Kaheil on 2010-10-10
Hello,

I've recently bought a netbook (a Compaq 700pe) and installed Ubuntu 10.10 (RC) on it. After finishing the installation, driver installation and update, I went to check the wireless device's MAC address in order to connect to my router, protected with mac filtering. 

And then, surprise, there were two interface, eth0 and eth1, two mac addresses (whom I put into the router's withelist) and none of them worked on wireless. 

I then tried to use the "Cloned Mac Adress" & "Device Mac Adress" options, but none worked. 

Therefore, I would need a software that allows me to either see the MAC address being sent to the router or a software to create a fake MAC address to be sent to the router. 

Help me! :D 

PS: the router is an old U.S. Robotics, almost 10 years old since it was first launched.

---

### Post by Iowan on 2010-10-10
Post results of **ifconfig -a**

---

### Post by johngreth on 2010-10-10
Cloned Mac Adress changes the mac address of the router, not the computer.

adding the HWaddr values from **ifconfig -a** should have worked. Not sure about that.

You can change the mac address if you need to by right clicking the networking icon and clicking edit connections. Then edit the applicable wireless connection and enter a new mac address.

Iowan is right. **ifconfig -a** may give us more insight.

---

### Post by Kaheil on 2010-10-10
eth0      Link encap:Ethernet  HWaddr 00:22:64:83:e1:61  
          inet addr:192.168.123.101  Bcast:192.168.123.255
Mask:255.255.255.0
          inet6 addr: fe80::222:64ff:fe83:e161/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:903917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1276344414 (1.2 GB)  TX bytes:21366673 (21.3 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:24:2b:40:28:d7  
          inet6 addr: fe80::224:2bff:fe40:28d7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:41
          TX packets:0 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4432 (4.4 KB)  TX bytes:4432 (4.4 KB)

---

### Post by johngreth on 2010-10-10
And you have added 00:22:64:83:e1:61 ?

Is there any other security on your router that may be causing a problem?

---

### Post by Kaheil on 2010-10-10
I've added both 00:22:64:83:e1:61 and 00:24:2b:40:28:d7 to the withelist. The first one allowed me to connect with an rj45 wire. 

And yes, I believe the problem lies in the router and not with Ubuntu. However, since I cannot afford a new router at the moment, tricking the router using Ubuntu seems the best solution.

---

### Post by johngreth on 2010-10-10
Have you tried disabling the mac filter to see if you can connect? That may not be the problem.

---

### Post by Kaheil on 2010-10-10
Very good point. I actually tried disabling the macfiltering and the problem continued, so I'll try changing the drivers for wireless.

---

### Post by Kaheil on 2010-10-10
Alright, I've changed the drivers from STA to B43 (and a new network appered), but I still can't connect to my router, MAC filtering or not.

Edit: when I tried connecting to another network, protected by a wep, I got an error message saying the key was incorrect, I therefore deduce that the netbook must have "talked" with the other router)

---

