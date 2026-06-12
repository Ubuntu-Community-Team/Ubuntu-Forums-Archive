---
title: "Help at wits end with network manager"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by intouchnathan on 2009-04-06
Okay heres the scoop i wanted to install wicd but you have to uninstall network manager to do that so i did. it has been a while for me with linux by the way. so when i go to install wicd it needs to connect to the internet to do so but my machine will not let me i cant find out where to go to get that done. i dont have the network option under admin setting and i cant remeber how to get it to connect wired through terminal. please help need my machine on  ASAP

---

### Post by intouchnathan on 2009-04-06
aslo i got the 4 other istalles that i needs to install wicd but whne i got to the last to it needs each to bealready installed to install the other one like... python-wxversion wont install without python-wxgtk and vise versa scince i dont have the internet im kinda stuck please help.

---

### Post by superprash2003 on 2009-04-06
post output of **ifconfig** from the terminal.. type **sudo dhclient eth0** where eth0 is the wired interface

---

### Post by intouchnathan on 2009-04-06
thank you so much i finally got wicd to install and run now to the next problem i have wireless built into my laptop but wicd says that " no wireless networks found" i know it sees the driver because under hardware drivers it shows it and says that it is active or in use my settings for wic re ndiswapper and wlan0 thank you in advance....

---

### Post by intouchnathan on 2009-04-06
wired still works but cant get wicd to show wireless networks and i cant even tell if acer wireless driver even works

---

### Post by intouchnathan on 2009-04-06
nathan@nathan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:e7:3c:f5  
          inet addr:192.168.1.7  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fee7:3cf5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8764 errors:0 dropped:978832033 overruns:0 frame:0
          TX packets:5886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5777480 (5.7 MB)  TX bytes:1077692 (1.0 MB)
          Interrupt:219 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4092 (4.0 KB)  TX bytes:4092 (4.0 KB)

---

