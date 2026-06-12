---
title: "no internet connection when i leave the live cd"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by sway.jd on 2009-04-01
hello there, need your help.

here is the thing, the first time I booted to the live cd i have internet connection. then I do the installation and when i leave the live cd to go to my full installation there is just no internet connection.

it says the network manager isn't working or something like that.

i'm using 9.04 beta x64.


any idea? want me to try the 32bit version?

---

### Post by freonchill on 2009-04-01
if you have 64bit hardware (and you do as it would not allow you to install 64bit on 32bit hardware)

if this everytime you boot or just the first time (e.g. have you rebooted since you installed)?

if so, please post your ifconfig output

---

### Post by sway.jd on 2009-04-02
since my lack of experience and ideas i tried the 32 bits version. but this time I have got no internet connection on the live cd.

the same thing happens, the simbol for wireless conection appearsnext to the clock with a red x on it and if i mouseouver its says network manager disabled but if I press it the network enabled is ticked.

also I get a crash report saying that exact same thing, network manager isnt working.

my ifconfig

eth0      Link encap:Ethernet  HWaddr 00:22:15:2c:cb:85  
          inet6 addr: fe80::222:15ff:fe2c:cb85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:3927 (3.9 KB)  TX bytes:3082 (3.0 KB)
          Interrupt:251 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:592 (592.0 B)  TX bytes:592 (592.0 B)

---

### Post by superprash2003 on 2009-04-02
type **sudo dhclient eth0** in your terminal and post output

---

### Post by sway.jd on 2009-04-02
> **superprash2003 said:**
> type **sudo dhclient eth0** in your terminal and post output



my problem is gone after i do this. thanks!

---

