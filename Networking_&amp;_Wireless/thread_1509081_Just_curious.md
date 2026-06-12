---
title: "Just curious"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by jmore9 on 2010-06-13
I have the following output from Kernel IP routing table :

I have comcast internet no router.

Destination - Gateway -    Genmask      Flags Metric Ref    Use Iface
71.205.112.0    0.0.0.0   255.255.240.0   U     1      0     0   eth0
169.254.0.0     0.0.0.0   255.255.0.0     U     1000   0     0   eth0
0.0.0.0      71.205.112.1    0.0.0.0      UG    0      0     0   eth0

Is this normal ?  Why does it go to 169.254.0.0 ?  71.205.112.1 is the default route .  Never seen this before just wondering why now ?

Thanks in advance for anyones help explaining the above.



Added the following --

Registering new address record for 192.168.100.10 on eth0.IPv4

and this

DHCPREQUEST of 192.168.100.10 on eth0 to 255.255.255.255 port 67

and this

Registering new address record for 192.168.100.10 on eth0.IPv4

Withdrawing address record for 192.168.100.10 on eth0

Those are router addys if i am not mistaken.  As i said above i have no router connected.  And it is not the address of the cable modem.

Also the following :

Also when i first start up i get an internet connection established notice from network manager , then about 20 secs later , i get dis-connected message , and after a few seconds i get connected  again.  Strange.

---

### Post by Iowan on 2010-06-13
The 169.254.0.0 is **avahi** (or link-local or zeroconf). My routing table looks similar - although I have a router, and other addresses are in 192.168.X.X.

---

### Post by jmore9 on 2010-06-13
Ok that explains that but what is the 192.168.100.10 ?  Modem is not at that address.  Hmm

---

