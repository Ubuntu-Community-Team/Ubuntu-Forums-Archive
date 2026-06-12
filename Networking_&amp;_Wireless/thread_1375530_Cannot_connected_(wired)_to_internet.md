---
title: "Cannot connected (wired) to internet"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by oospill on 2010-01-08
I just got a new power supply in my old desktop, and installed ubuntu on it.
I've got three NICs in there (for a later project), and when I connect my cable modem to any one of the NICs, then little connection triangle-spinny-thing in the upper-right tries to connect.  But it never gets all the way connected.

Any ideas?
thanks

---

### Post by 98cwitr on 2010-01-08
when you do an ifconfig, is the DHCP assigning an IP?

---

### Post by oospill on 2010-01-08
Here's what it says when I do 'ifconfig' : (With the cable modem hooked to eth0)
=======================================================================

eth0      Link encap:Ethernet  HWaddr 00:1c:f0:0e:a4:8f  
          inet6 addr: fe80::21c:f0ff:fe0e:a48f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:262680 (262.6 KB)  TX bytes:3204 (3.2 KB)
          Interrupt:17 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:1c:f0:16:3f:43  
          inet6 addr: fe80::21c:f0ff:fe16:3f43/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:622320 (622.3 KB)  TX bytes:2520 (2.5 KB)
          Interrupt:18 Base address:0x2400 

eth2      Link encap:Ethernet  HWaddr 00:1c:f0:0b:84:60  
          inet6 addr: fe80::21c:f0ff:fe0b:8460/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:16178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:970680 (970.6 KB)  TX bytes:3888 (3.8 KB)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3184 (3.1 KB)  TX bytes:3184 (3.1 KB)

---

### Post by Project PWNED on 2010-01-08
dhclient eth0 or whatever one is plugged in, will fetch it a new IP address. It looks like that is the problem.

---

### Post by Iowan on 2010-01-08
If the machine is connected directly to the modem (no router in between), you *might* need to power-cycle the modem (turn it off for about a minute, then back on. Some modems "lock onto" the MAC address and won't service another one.

---

### Post by oospill on 2010-01-08
Thanks, Iowan .. I hit the little reset button on my cable modem, rebooted my machine, and now I'm typing on it. =)

thanks!

---

