---
title: "UBUNTU 10.04 wireless network problem"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by sv12345 on 2010-10-18
Hello everybody
I'm using an inspiron 6400 Dell laptop 
I installed ubuntu 10.04 yesterday
It has 2 main problems one of them is that it can't show installed drivers and the other one is that it has a really important problem with my wireless net driver(Dell 1390 Wlan Driver)
I've done so much I mean I've tried many ways such as windows driver installer packeges in ubuntu but it doesn't work
when I check the net status (sudo lshw -c network) it says that wireless is disabled but I'm very doubtful if it is really detected at all
I think the main problem is the bcmwl package(5.6 version) and when I tried to reinstall it it didn't work
I will be really thankful if anyone can give me a hand about this

---

### Post by TBABill on 2010-10-18
Ok, first how did you get the Broadcom driver installed the first time? Was it via Synaptic or did you try via download from the net? Be as specific as you can.
 
Run: ```
iwconfig
```
 
in a terminal and post the output. That will help identify your wireless device and status.
 
Are you able to connect via ethernet to a router or cable/DSL modem? If you can it is possible you can download and enable the driver via System>Applications>Hardware

---

### Post by sv12345 on 2010-10-19
Hello 
thanks for your suggestion
I've checked 10.1 ver and it detects my wireless driver
but the problem is that it's not installed , while i'm trying to install it my system hangs and I'm so angry about ubuntu:mad:

---

