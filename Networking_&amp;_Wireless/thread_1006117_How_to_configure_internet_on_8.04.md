---
title: "How to configure internet on 8.04 ?"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by ivanhoe75 on 2008-12-09
How to configure internet on 8.04 without bending to mac address?
ethernet plug. It works perfectly with banding to mac address, but no working without. Windows works both variants.

---

### Post by prshah on 2008-12-09
> **ivanhoe75 said:**
> How to configure internet on 8.04 without bending to mac address?
ethernet plug. It works perfectly with banding to mac address, but no working without. Windows works both variants.

Ubuntu will work as well. If you are using gnome (and hence network manager), right click the network manager icon, then click "Edit Connections.." and add a network connection with blank MAC address.

Post back if you still have difficulties.

---

### Post by murrayd77 on 2008-12-09
If its a adsl router in Ubuntu: System > Select Administration and select Network. Click unlock and provide your password. After logging in, mark Wired connection as active and yes, its now connected.

---

### Post by ivanhoe75 on 2008-12-09
Network options are unaccessible - gray button. Some avahi and network manager are installed, some not. Do you know what tools to install? Forget, I have to be root, I'll try under root.OOh NO!! no work under root.
I see wrong IP (not IP given by provider) I unblock adjustment change IP and it absolutely doesnt working

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:04:61:71:b4:16  
          inet addr:195.112.125.227  Bcast:195.112.125.255  Mask:255.255.255.128
          inet6 addr: fe80::204:61ff:fe71:b416/64 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1057;&#1089;&#1099;&#1083;&#1082;&#1072;
          &#1042;&#1042;&#1045;&#1056;&#1061; BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4392 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2751 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:1000 
          RX bytes:3827978 (3.6 MB)  TX bytes:396145 (386.8 KB)
          &#1055;&#1088;&#1077;&#1088;&#1074;&#1072;&#1085;&#1086;:16 Base address:0xc000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:&#1059;&#1079;&#1077;&#1083;
          &#1042;&#1042;&#1045;&#1056;&#1061; LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9656 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9656 errors:0 dropped:0 overruns:0 carrier:0
          &#1082;&#1086;&#1083;&#1083;&#1080;&#1079;&#1080;&#1080;:0 txqueuelen:0 
          RX bytes:482800 (471.4 KB)  TX bytes:482800 (471.4 KB)


Probem is solved in later release. Admin, delete this thread, please

---

