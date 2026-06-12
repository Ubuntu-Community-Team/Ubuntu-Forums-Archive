---
title: "There was an error copying the file into smb:// PcName/Folder/Folder"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by morbid_bean on 2009-06-14
When I try to copy a file over my wireless network from my ubuntu to a windows vista machine it will pop this error up shortly after the transfer starts.

```
There was an error copying the file into smb:// PcName/Folder/Folder

Details:  Connection timed out
```

---

### Post by morbid_bean on 2009-06-14
Bump!   Anyone?

---

### Post by superprash2003 on 2009-06-14
try replacing pcname with pcip

---

### Post by morbid_bean on 2009-06-14
> **superprash2003 said:**
> try replacing pcname with pcip

well I actually browse it buy using natilus

---

### Post by jimv on 2009-06-15
I saw a similar bug that was resolved by updating Vista to SP1.  Also, Vista SP2 is out.  Perhaps try getting Vista as up to date as you can, then try again and let us know what happens.

---

### Post by superprash2003 on 2009-06-15
post output of ifconfig from ubuntu terminal

---

### Post by morbid_bean on 2009-06-15
> **superprash2003 said:**
> post output of ifconfig from ubuntu terminal

```
eth0      Link encap:Ethernet  HWaddr 00:30:1b:31:e1:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x2d00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:9e:ff:83  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7eff:fe9e:ff83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2048927 (2.0 MB)  TX bytes:521859 (521.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-7E-9E-FF-83-66-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by morbid_bean on 2009-06-16
> **jimv said:**
> I saw a similar bug that was resolved by updating Vista to SP1.  Also, Vista SP2 is out.  Perhaps try getting Vista as up to date as you can, then try again and let us know what happens.

Dude... your the best, it worked after SP1 upgrade \\:D/

---

