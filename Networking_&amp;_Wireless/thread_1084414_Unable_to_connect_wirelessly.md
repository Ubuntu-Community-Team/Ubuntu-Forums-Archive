---
title: "Unable to connect wirelessly"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by ufarmer on 2009-03-02
I just installed Ubuntu 8.10 on my laptop.  It detects my wireless router, asks for the password, and claims to make a connection, but Firefox is unable to connect to any websites.  The router is definitely connected to the internet and the "broadcast" indicator LED is lit.  Any advice is appreciated.

---

### Post by Atrophy on 2009-03-02
Try this, worked for me:

First, find a wired connection. Connect to that, and then run your package manager and install all updates and program fixes and whatnot. Then open terminal and run 'sudo apt-get install linux-backports-modules-intrepid-generic' and reboot.

---

### Post by ufarmer on 2009-03-02
Thanks, I'll try that.

I have a related question.  When I plug the laptop into the router directly with an ethernet cable, it is able to use the connection only after a reboot.  Is there any way to detect/use the DSL connection without rebooting?

Correction: It *was* able to see the connection after reboot.  Now it can't find the connection at all.

---

### Post by Atrophy on 2009-03-02
When trying to connect via cable directly into the router, what is the result of "sudo ifconfig"?

---

### Post by ufarmer on 2009-03-10
Sorry to take so long getting back to you.  Here's the output of sudo ifconfig.  I double checked and the laptop is definitely unable to detect and use the direct link.

eth0      Link encap:Ethernet  HWaddr 00:1c:25:a0:53:b9  
          inet6 addr: fe80::21c:25ff:fea0:53b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Memory:fc200000-fc220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:ca:8e:5c  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:feca:8e5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:67734 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8471 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26375380 (26.3 MB)  TX bytes:2474608 (2.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-6B-CA-8E-5C-65-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

