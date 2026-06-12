---
title: "cannot connect ethernet"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by virenec on 2009-01-21
i have just installed ubuntu 8.10 in my laptop hp(au6502) along side windows vista bt i was unable to connect ethernet it simply said not connected.

i tried to change ip address for my settings but it get changed automatically....

how can i change ip address for wired connection?

---

### Post by Iowan on 2009-01-21
Post results of **ifconfig** and contents of */etc/network/interfaces*

---

### Post by virenec on 2009-01-22
viren@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:64:a2:fd  
          inet6 addr: fe80::21b:24ff:fe64:a2fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:294012 (294.0 KB)  TX bytes:4644 (4.6 KB)
          Interrupt:252 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:70:45:93  
          inet6 addr: fe80::21a:73ff:fe70:4593/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)



contents of /etc/network/interfaces

auto lo
iface lo inet loopback

---

### Post by zenial on 2009-01-22
Hmmmm. I had the same problem
enabling dhpc DID IT FOR ME
"ENABLE "DHPC" IN UR NETWORK MANAGER"

---

### Post by Iowan on 2009-01-22
[Here]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") is a How-To for static addresses in Intrepid.

---

### Post by virenec on 2009-01-26
i tried whatever was written over there. From that i was able to  set the static ip but when i connect the ethernet it didn't take the connection i have made it created a new connection named Auto Ethernet and again started finding ip from the network.

---

### Post by normanp on 2009-01-28
See my post in [http://ubuntuforums.org/showthread.php?t=1050965&page=2](http://ubuntuforums.org/showthread.php?t=1050965&page=2)
This makes NM work.

---

