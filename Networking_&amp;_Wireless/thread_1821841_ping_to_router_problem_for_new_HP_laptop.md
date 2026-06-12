---
title: "ping to router problem for new HP laptop"
date: 2011-08-09
forum: Networking &amp; Wireless
---

### Post by Arijit_Kundu on 2011-08-09
Hi guys,

I have a complicated problem. I recently bought a HP laptop which is showing some issues. To make it precise:

1. I can connect to ethernet & wireless when i am at my university, which are quite good connections. 

2. At my home, i share the internet with another guy. The connection is not very stable, in the sense that, sometimes the download speed is 1MiB/s, and sometime 250 KiB/s. I have a old laptop which can connect to it without any problem.

3. My new laptop can connect to it when the connection is better with download seed ~1MiB/s, but could not connect to it when the download speed goes down. 

4. "could not connect" means even ping to router takes long time with 90% packet loss. But I can always get connection and ip address from dhcp although i can not ping thereafter. This is true for wired & wireless connection both. 

Is that a router issue? but then, why can i connect through the other laptop. 

Here is my ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 64:31:50:a3:72:5a  
          inet6 addr: fe80::6631:50ff:fea3:725a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1140 errors:0 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:103749 (103.7 KB)  TX bytes:126936 (126.9 KB)
          Interrupt:47 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30864 (30.8 KB)  TX bytes:30864 (30.8 KB)

wlan0     Link encap:Ethernet  HWaddr bc:77:37:b0:ae:9b  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::be77:37ff:feb0:ae9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:301469 (301.4 KB)  TX bytes:88856 (88.8 KB)

```

---

### Post by poolet on 2011-08-09
Try to ping your localhost to see if your have a problem with your router...
A common problem of that is problem with your router/modem or it's  set for  half-duplex!!!

First check your modem/router first by pinging to your localhost... and if it's ok we will think about it!!! :)

---

### Post by Arijit_Kundu on 2011-08-10
the problem is, i dont have the access to the username/password for the router. So, i can not connect the router through web browser and login. Can i do something else from my computer without login to the router?

or, am i missing something?

---

### Post by poolet on 2011-08-10
just open a new terminal and ping  [FONT=monospace]192.168.0.102 and 127.0.0.1 first of all we need to ensure that your model/router is ok....[/FONT]

---

### Post by Arijit_Kundu on 2011-08-10
poolet, i am at work at the moment, i'll do what you said as soon as i reach my home..

sorry for the delay!

---

### Post by Arijit_Kundu on 2011-08-10
ping to 192.168.0.105 (has changed now) and 127.0.0.1 are working just fine. 

any ideas?

---

### Post by poolet on 2011-08-10
its seems that your problem has to do with metric.... 
Clear your dns cache  ```
ipconfig /flushdns
``` -  ```
ipconfig  /displaydns 
```- ```
lookupd -flushcache
``` - ```
sudo  /etc/init.d/networking restart 
```( This is nothing to do with your  network... Also login as root and ```
route -C 
```

---

### Post by Arijit_Kundu on 2011-08-10
thanks poolet, right now the network is fine as the speed is good. I'll do what you've said once the speed will be down. (i know its a funny problem!)

can you please subscribe to this thread? then, whenever the network will slow down i can write back to the thread.

---

### Post by poolet on 2011-08-11
Done :)

---

### Post by Arijit_Kundu on 2011-08-19
hi poolet, its a while now. I tried many steps to clearup dns cache etc, but at the end i am convinced that it is really a router issue. because: 1. i have a usb netgear adapter, which also does not work in slow speed, does not matter which computer i connect it to. 2. i dual booted with windows, and found the same problem there. SO, i am almost sure that its a router issue.

anyway, thank you a lot for giving your time!

---

