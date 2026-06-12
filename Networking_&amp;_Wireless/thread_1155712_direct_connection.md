---
title: "direct connection"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by groosam on 2009-05-11
Newer to networking.  Tried finding a similiar post, but unsuccesful

Trying connect internet through ethernet connection from modem (it's comcast high speed)...computer recognizes when I turn on/off modem but doesn't allow a connection

I do recieve signal when connected with the router, so there is a connection.

Please help.

---

### Post by withjigs on 2009-05-11
what sort of IP configuration are you using? 
dynamic (DHCP)or Manual ?
Can u post output of your "ifconfig" command ?
thanks...

---

### Post by groosam on 2009-05-11
I think dynamic...i'm not sure on the difference...

eth0      Link encap:Ethernet  HWaddr 00:23:5a:15:3b:65  
          inet6 addr: fe80::223:5aff:fe15:3b65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:164027 (164.0 KB)  TX bytes:13162 (13.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26170 (26.1 KB)  TX bytes:26170 (26.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:fa:3c:e2:44  
          inet6 addr: fe80::222:faff:fe3c:e244/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3873460 (3.8 MB)  TX bytes:715814 (715.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-FA-3C-E2-44-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Iowan on 2009-05-11
Is the router the DHCP server or is the modem?
(Sounds like the router is - since you "receive signal when connected with the router".

---

### Post by groosam on 2009-05-12
I'm sure your correct.

I have an airport express hooked to the modem.  I unhooked it from there and connected my comp straight to the modem...still nothing.

---

### Post by Iowan on 2009-05-12
Unless the modem also has a DHCP server, you may need to give the machine a static address.  It'll need to be in same subnet as modem - and I haven't a clue what address the modem might use.  My DSL modem does have a DHCP server, but I have it turned off in favor of my local server.
Is there a reason you don't want to leave the router in the circuit?

---

### Post by groosam on 2009-05-14
I'll try what you said
No real reason, maybe just for help in the future.

---

