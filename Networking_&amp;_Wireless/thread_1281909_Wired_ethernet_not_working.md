---
title: "Wired ethernet not working"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by r0xtehem0x on 2009-10-03
I'm using a wireless bridge to connect my PC to our wireless network.  I just installed Ubuntu 8.04 and I cannot access the internet.  I have checked the wireless bridge and it works on my eeepc running Windows XP.  The light is on for wireless activity, but the light is not on for PC activity.  So I'm not getting internet access via my wired connection.  Any solutions?


ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:07:e9:c2:8c:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124336 (121.4 KB)  TX bytes:124336 (121.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:86:b2:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-86-B2-55-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by kreggz on 2009-10-06
Your not getting an IP address, you could try hardcoding one.

What type of network card do you have? type lspci in the terminal and post it here

---

### Post by r0xtehem0x on 2009-10-06
```
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
```

I have a wireless card also, I just got that working.  So my problem with being able to access the internet is solved.  Though, I'm still working on trying to fix my wired connection for future reference.

---

### Post by kreggz on 2009-10-06
try this:

disconnect the wifi, plug in your ethernet cable and type this in the terminal: ifconfig. post the output of the command.

---

