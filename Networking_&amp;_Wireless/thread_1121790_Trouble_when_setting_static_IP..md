---
title: "Trouble when setting static IP."
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by BramWillemsen on 2009-04-10
Hello everyone,

I've used DHCP on my laptop for some time, but i tried switching to a static IP yesterday in order to make opening ports a bit easier. But every once in a while my connection just gets lost. No pings reach my router for ~15 seconds and then everything works fine again. There is no such trouble when im using DHCP.

These are the settings i used, 

my IP 192.168.1.20
subnet 255.255.255.0
gateway 192.168.1.1
dns 192.168.1.1

192.168.1.1 is my router. I use exactly the same settings on my desktop computer (except for another IP ofcourse), and i don't get these timeouts. Is there something wrong with these settings? I'm not that experienced so i may overlook something:)

ty

---

### Post by superprash2003 on 2009-04-10
check the DHCP range in your router.. and ensure that your static ip is outside its DHCP range..

---

### Post by BramWillemsen on 2009-04-10
Thanks for the suggestion. I did, and the DHCP range starts at 100, so 20 should be safe i guess.

---

### Post by BramWillemsen on 2009-04-10
i guess my last message wasn't very clear. I meant that i **should** be safe outside the DHCP zone when i turn on static IP. I still get these massive ping losses occasionaly though. No response for seconds, webpages stop loading etc.

---

### Post by BramWillemsen on 2009-04-11
does anyone have an idea ?:)

---

### Post by superprash2003 on 2009-04-11
post output of ifconfig from the terminal

---

### Post by BramWillemsen on 2009-04-18
okay here it is:

eth0      Link encap:Ethernet  HWaddr 00:22:64:71:86:7e  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:64ff:fe71:867e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1420479 (1.4 MB)  TX bytes:217707 (217.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

---

