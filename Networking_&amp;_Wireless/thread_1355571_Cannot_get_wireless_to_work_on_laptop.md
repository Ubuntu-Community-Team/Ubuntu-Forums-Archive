---
title: "Cannot get wireless to work on laptop"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Mr Williams on 2009-12-15
Hello Everybody

I have just come from windows, dont hate me, but I am definetly enjoying xubuntu for the most part.  The only problem I have is getting my wireless card to run inside my laptop.  

The card is a **Broadcom Corporation BCM4312 802.11a/b/g (rev 01)** according to lspci

I have tried using the ndiswrapper tutorials, but find it very complicated, terms such as 'tarring' and 'sudo' are alien to me.  The broadcom linux driver is also difficult to follow, could someone help me out?

---

### Post by Mr Williams on 2009-12-15
*Update*

I managed to get it working , but it runs noticbly slower then when it was under vista, why is this?

---

### Post by lidex on 2009-12-15
Can you run these commands in a terminal and post the output?
```
lspci | grep -e Ethernet -e Wireless
```
```
ifconfig
```

Copy and paste commands into terminal: "Accessories>Terminal". Copy and paste output text, highlight and click on "#" above.

---

### Post by Mr Williams on 2009-12-15
> **lidex said:**
> Can you run these commands in a terminal and post the output?
```
lspci | grep -e Ethernet -e Wireless
``````
ifconfig
```Copy and paste commands into terminal: "Accessories>Terminal". Copy and paste output text, highlight and click on "#" above.


```
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)

```

```
eth0      Link encap:Ethernet  HWaddr 00:16:d4:a2:16:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth2      Link encap:Ethernet  HWaddr 00:1a:73:08:29:68  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe08:2968/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:225399 errors:0 dropped:0 overruns:0 frame:4126
          TX packets:169005 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:299640581 (299.6 MB)  TX bytes:15654865 (15.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44476 (44.4 KB)  TX bytes:44476 (44.4 KB)
```

---

### Post by lidex on 2009-12-15
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=1352270&highlight=broadcom")

---

