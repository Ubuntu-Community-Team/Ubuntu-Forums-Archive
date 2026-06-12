---
title: "Network not working"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by yellowzelo on 2011-05-03
Hi,

I needed to free up some disk space and according to tutorial DietUbuntu ([https://help.ubuntu.com/community/Diet%20Ubuntu](https://help.ubuntu.com/community/Diet%20Ubuntu)) I removed following packages: 

```
ppp pppconfig pppoeconf wvdial
```

Since then my wifi and ethernet connections doesnt work. Installing those packages on system didnt help.

Here are outputs of some commands:

```
martin@compal:~$ sudo ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39565 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1156417 (1.1 MB)  TX bytes:1156417 (1.1 MB)
```

```
martin@compal:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
```

```
martin@compal:~$ ping www.google.com
ping: unknown host www.google.com
```

What should I do?
Thank you!

---

