---
title: "network interface numbering messed up"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by agarzon on 2010-10-06
Hi, I am trying to get my ethernet adapter list to make some sense. This is what ifconfig spits out

```
agarzon@euler:~$ ifconfig 
eth3      Link encap:Ethernet  HWaddr b8:ac:6f:3b:f4:4f  
          inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe3b:f44f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13757 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5158363 (5.1 MB)  TX bytes:812446 (812.4 KB)
          Interrupt:17 

eth4      Link encap:Ethernet  HWaddr 90:4c:e5:b2:d6:24  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ::924c:e5ff:feb2:d624/64 Scope:Global
          inet6 addr: fe80::924c:e5ff:feb2:d624/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5028 errors:0 dropped:0 overruns:0 frame:19011
          TX packets:68 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:552561 (552.5 KB)  TX bytes:11899 (11.8 KB)
          Interrupt:56 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:138713 (138.7 KB)  TX bytes:138713 (138.7 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.52.1  Bcast:192.168.52.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.117.1  Bcast:192.168.117.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

agarzon@euler:~$ 

```

What I need, is for the OS to read eth3 as eth0, as it originally did after install. Any clues on how to do this?

The reason I am asking about this is I have a piece of software whose license is tied to the IP on eth0

---

### Post by BkkBonanza on 2010-10-06
The ethX numbers are assigned by udev rules. If you switch adapters then  the old rules get left behind and new ones created that increment the number. You would have to go into the rules file and remove old rules, and/or manually adjust them to suit your needs.

The file to check is **/etc/udev/rules.d/70-persistent-net.rules**

Once you look at it you can probably see how to change the numbering or simply remove the old rules and allow a new one to be created upon boot.

---

### Post by agarzon on 2010-10-07
BkkBonanza:

Thanks for your reply. Exactly what I needed. I modified  the file manually:

```
sudo vi /etc/udev/rules.d/70-persistent-net.rules
```

reordered the interfaces, rebooted and everything is as I want it to be.

Thanks again.

---

