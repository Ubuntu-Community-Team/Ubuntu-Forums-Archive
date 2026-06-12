---
title: "wifi card appears as eth0"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by jareddlc on 2009-08-24
I have a HP mini 1000 with a b43. My ifconfig

eth0      Link encap:Ethernet  HWaddr 00:24:2b:7a:c1:93  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe7a:c193/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:7130 errors:0 dropped:0 overruns:0 frame:96254
          TX packets:6818 errors:17 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3993618 (3.9 MB)  TX bytes:1064368 (1.0 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3845 (3.8 KB)  TX bytes:3845 (3.8 KB)

i can access everything fine, but only when i want to put my card into monitor mode it wont let me since it thinks its an Ethernet card which is cleary a wireless. any ideas how to change eth0 to wlan0 in ubuntu 9.04

---

### Post by Tclarkie on 2009-08-24
r u running ubuntu natively?

---

### Post by shanix on 2009-08-24
> **jareddlc said:**
> since it thinks its an Ethernet card which is cleary a wireless. 

How can you tell if the card is a wire or wireless by just using the ifconfig command??

---

### Post by Iowan on 2009-08-24
> **shanix said:**
> How can you tell if the card is a wire or wireless by just using the ifconfig command??May not be able to by **ifconfig** alone, but if it's working fine with no cable connected, there's a good chance it's a wireless card.  My HP laptop also has wireless card defined as eth - in my case, the wired card is eth0, the wireless card is eth1.  Since it does what I need, I haven't seen fit to change it.

---

### Post by jareddlc on 2009-08-25
yes its my wifi card since i can connect to the internet without a wire :)

---

