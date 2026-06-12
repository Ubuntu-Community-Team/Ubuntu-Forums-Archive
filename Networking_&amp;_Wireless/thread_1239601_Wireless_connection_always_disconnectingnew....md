---
title: "Wireless connection always disconnecting/new..."
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by vickoxy on 2009-08-13
Hi,
wanted to post reply here;
[http://ubuntuforums.org/showthread.php?t=522808](http://ubuntuforums.org/showthread.php?t=522808)
but i couldn´t do it.

So i have the same problem. Every 5-10 min my wifi disconnects itself.
```

++++@Mini9:~$ lspci -nn | grep Ethernet04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
++++@Mini9:~$ lspci -nn | grep Network03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

++++@Mini9:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```


This problem i did not notice using Dell´s Hardy. Now i am using Ubuntu 9.04 2.6.28-14-generic on dell mini 9.

Is there some workaorund?

Thanks

---

### Post by vickoxy on 2009-08-13
Almost same here-if i wait log enough it reconnect itself:

[http://ubuntuforums.org/showthread.php?p=7680546](http://ubuntuforums.org/showthread.php?p=7680546)

---

### Post by vickoxy on 2009-08-13
```
@Mini9:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:21:70:d2:62:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

eth1      Link encap:Ethernet  Hardware Adresse 00:23:08:2c:3f:a2  
          inet Adresse:192.168.1.3  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::223:8ff:fe2c:3fa2/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:18884 errors:0 dropped:0 overruns:0 frame:1503
          TX packets:15725 errors:6 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:19226491 (19.2 MB)  TX bytes:2527463 (2.5 MB)
          Interrupt:17 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:1800 (1.8 KB)  TX bytes:1800 (1.8 KB)
```

---

