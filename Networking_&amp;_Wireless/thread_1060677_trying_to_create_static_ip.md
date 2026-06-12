---
title: "trying to create static ip"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by -jay- on 2009-02-05
hi im trying to setup a static ip in network manager well i everything i do i end up losing my connection btw im using a wired connection no router

heres the result from ifconfig 
```

jay@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:e6:86:92:73  
          inet addr:76.93.49.251  Bcast:76.93.51.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:980036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:288268440 (288.2 MB)  TX bytes:37836691 (37.8 MB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10573 (10.5 KB)  TX bytes:10573 (10.5 KB)

jay@ubuntu:~$ 
```


thanks in advance

---

### Post by Iowan on 2009-02-05
See if [this]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") How-To helps.

---

### Post by punx45 on 2009-02-06
looks like you are connected directly to an ISP, road runner from the looks of it.   i dont think you can specify your own IP in that case.

---

### Post by wlraider70 on 2009-02-06
I spent a lot of time working on that. I just got it settled.

[http://ubuntuforums.org/showthread.php?t=1054410](http://ubuntuforums.org/showthread.php?t=1054410) 
this is some of my exp.

in the end Iowan was right, two posts up.

---

