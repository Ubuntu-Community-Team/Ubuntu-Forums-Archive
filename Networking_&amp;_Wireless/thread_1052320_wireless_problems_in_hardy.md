---
title: "wireless problems in hardy"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by li0id on 2009-01-27
I'm tring to get my atheros communications inc. ar242x 802.11 abg wireless pci express adapter [168c:001c] card to work. i followed a thread that told me how to do it, but it still doesn't work. when i run ifconfig this is what i get:

```
root@laptop:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:8b:39:a6:b7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:1114619899 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5233 (5.1 KB)  TX bytes:5013 (4.8 KB)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80200 (78.3 KB)  TX bytes:80200 (78.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:79:42:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:55200000-55210000 

```

can someone please tell me what is wrong? thanks in advanced.`

---

### Post by li0id on 2009-01-27
btw i just restarted my computer and when i ran ifconfig, it states no wlan0.

michael@laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:8b:39:a6:b7  
          inet addr:172.16.16.115  Bcast:172.16.16.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe39:a6b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2023 errors:0 dropped:1116706534 overruns:0 frame:0
          TX packets:1135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2543859 (2.4 MB)  TX bytes:206947 (202.0 KB)
          Interrupt:220 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70900 (69.2 KB)  TX bytes:70900 (69.2 KB)


does anyone know why that has happen now. also when i go into the ndisgtk is use to state that my hardware was detected, but now it says its not.

thanks in advanced for anyone that can help.

---

### Post by li0id on 2009-01-27
bump

---

### Post by sowelie on 2009-01-27
What kind of wireless card do you have?  Have you checked System -> Administration -> Hardware Drivers to make sure there isn't a closed source driver available for your wireless adapter?

---

