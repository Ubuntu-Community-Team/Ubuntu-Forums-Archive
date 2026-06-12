---
title: "Can't get outside!"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by Hawk__0 on 2009-04-13
Running Ubuntu Server (8.10?) in a virtual machine, and for whatever reason it can ping everything EXCEPT things outside the network (IE: google.ca).  it shuts me down with "ping: unknown host www.google.ca".

/etc/resolv.conf has the appropriate entries:

cat /etc/resolv.conf 
nameserver 192.168.12.243
nameserver 192.168.12.30
nameserver 65.39.152.237

.243 is a PDC with DNS on it, a Windows Server 2003 box.

eth2 config:

eth2      Link encap:Ethernet  HWaddr 08:00:27:14:95:4a  
          inet addr:192.168.12.248  Bcast:192.168.12.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe14:954a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2517 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2458829 (2.3 MB)  TX bytes:895025 (874.0 KB)
          Base address:0xc010 Memory:f0000000-f0020000


EDIT:

This thread shows basically my problem:
[https://www.linuxquestions.org/questions/linux-networking-3/cannot-ping-outside-intranetlan-64628/](https://www.linuxquestions.org/questions/linux-networking-3/cannot-ping-outside-intranetlan-64628/)

except its not for ubuntu and im not sure on what to do.  my route -n shows:
 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.12.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2


when i try and delete 0.0.0.0 it doesnt work.  the gateways is 192.168.12.253

---

### Post by Iowan on 2009-04-13
What's in your */etc/network/interfaces* file?

---

### Post by Hawk__0 on 2009-04-13
I found an answer here:
[http://ubuntuforums.org/showthread.php?t=432999](http://ubuntuforums.org/showthread.php?t=432999)

---

