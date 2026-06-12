---
title: "Need help (fast)"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by qbox on 2009-02-14
Hi
I have one laptop and I put ubuntu 8.04 on it. I configure the network like I did before. I set the DNS. I can ping any website and any computer on the network. But I only can open google.com. I cant open anything else. The pings work great. Any help. THX.

---

### Post by superprash2003 on 2009-02-14
try changing DNS servers to opendns - 208.67.222.222 and 208.67.220.220. .. post output of **ifconfig** from the terminal

---

### Post by qbox on 2009-02-14
```
qbox@qbox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:3d:a7:12  
          inet addr:172.18.10.98  Bcast:172.18.10.255  Mask:255.255.255.0
          inet6 addr: 2002:d432:412a:4:21c:23ff:fe9d:7e1c/64 Scope:Global
          inet6 addr: fec0::4:21c:23ff:fe9d:7e1c/64 Scope:Site
          inet6 addr: fe80::21c:23ff:fe9d:7e1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:996808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88913 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:227399244 (216.8 MB)  TX bytes:646811 (631.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:880155 (859.5 KB)  TX bytes:880155 (859.5 KB)

```

I try with open dns... same stuff. I can ping but I cant open nothing. :S

---

### Post by qbox on 2009-02-14
I try and with ubuntu 8.10
same
I can open only google.....
nothing else :S
I need help quick
Please.

---

### Post by superprash2003 on 2009-02-15
you could try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

