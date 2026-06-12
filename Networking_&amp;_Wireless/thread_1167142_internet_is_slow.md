---
title: "internet is slow"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by kehon on 2009-05-22
i'm connected to a netgear router from my ahteros chip and the internet speed keeps fluckating and its not the router or whatever because on windows its the same speed and is ok but on ubuntu it is slower at times one time i got it to work by disconnecting an reconecting serveral times can anyone help solve this

---

### Post by kehon on 2009-05-22
i think firewall may be slowing me down how can i configure it correctly i installed firestarter a while ago and i believe thats the problem but its only a guess

---

### Post by nikgare on 2009-05-22
Have you tried the restricted driver instead?
I too have an Atheros chip and mine only started working properly after installing the driver via System->Administration->Hardware Drivers

---

### Post by kehon on 2009-05-22
it offers madwifi but i enable and restart and its disabled again so how do i enable

---

### Post by superprash2003 on 2009-05-23
i dont think its firestarter .. in your terminal type ifconfig and post output..

---

### Post by Crafty Kisses on 2009-05-23
Is it possible that you have IPv6 enabled? You could try and seeing if the IPv6 module is being used by running the following:
```
lsmod | grep ipv6
```

---

### Post by kehon on 2009-05-23
```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:ee:53:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10064 (10.0 KB)  TX bytes:10064 (10.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:91:db:43  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe91:db43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1982 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1981086 (1.9 MB)  TX bytes:354414 (354.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-4C-91-DB-43-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by sc0g on 2009-05-23
If just browsing the internet is slow, I'd suggest changing your DNS servers... You'd be amazed at how much your browsing speed increases if you use a good DNS server. I use OpenDNS rather than what my ISP assigns, because they tend to use Winders' servers as DNS servers, which is just overkill in my opinion.

Here are the DNS servers I use. You can update /etc/resolv.conf incase you don't want to change the DNS server settings on your router:

nameserver 205.152.37.23
nameserver 205.152.132.23

---

### Post by kehon on 2009-05-23
cool thanks thats helpful and actually seems a little faster not much though

---

### Post by superprash2003 on 2009-05-24
as mentioned by codename , you could also try disabling ipv6

---

