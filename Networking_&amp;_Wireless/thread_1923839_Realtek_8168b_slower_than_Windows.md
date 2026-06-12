---
title: "Realtek 8168b slower than Windows"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by clickwir on 2012-02-11
I dual boot Kubuntu and Windows 7. Installed the r8168 driver and rmmod the r8169 driver in Kubuntu. Windows, I installed the driver from the CD that came with the motherboard. 

When in Windows, transferring a few gigabytes from my Samba server, I get 70-80MB/sec. When in Kubuntu, it's 6-9MB/sec. 

Jumbo frames is enabled at 9k in both Windows and Kubutnu.

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.x.x  Bcast:192.168.x.255  Mask:255.255.255.0
          inet6 addr: fe80::ca60:ff:fexx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1

Any suggestions?

---

### Post by inobe on 2012-02-11
try that from linux to linux, just to test :D

---

### Post by clickwir on 2012-02-11
The samba server is Ubuntu Server. But it's using a e1000e driver.

---

### Post by inobe on 2012-02-12
from the looks of it, i would say use different hardware if this ins't a laptop, heck, a quick google search reveals countless problems from it.

i would dump it in a new york minute!

---

### Post by clickwir on 2012-02-12
that sucks. Its the onboard. I'd think that something with actual drivers from the manufacturer would perform better than this. :-/

Guess I'll have to see about spending $30 on a decent NIC.

---

