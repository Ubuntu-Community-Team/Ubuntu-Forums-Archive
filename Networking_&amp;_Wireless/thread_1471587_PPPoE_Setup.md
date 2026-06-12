---
title: "PPPoE Setup"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by cahoseg on 2010-05-03
Hi. I'm relly new to Ubuntu 10.4 LTS and I have PPPoE connection through DSL Extreme. Does anyone know how to set this up properly? I have a separate partition for my Windows XP and, well, I followed their instructions how to set it up but and is currently working for me on XP but they dont have anything for linux users. Thanks.

---

### Post by dwhinkl on 2010-05-18
> **cahoseg said:**
> Hi. I'm relly new to Ubuntu 10.4 LTS and I have PPPoE connection through DSL Extreme. Does anyone know how to set this up properly? I have a separate partition for my Windows XP and, well, I followed their instructions how to set it up but and is currently working for me on XP but they dont have anything for linux users. Thanks.

I set up a DSL Extreme PPPoE account this afternoon. (wired from modem to ethernet port) Here is how I did it...

Go to "System/Preferences/Network Connections

Select "DSL" tab
Select "ADD"
Fill in desired connection name
Fill in the username and password given to you by DSL Extreme (or your own if you changed it)
In the "Service" field input "dslextreme.com" without the quotes

On the bottom of the modem that was supplied by DSL Extreme note it's MAC address and write it down.

Select "Wired" tab and then enter that MAC address in the "MAC address" field. NOTE colons must be used between MAC address fields ... 00:00:00:00:00:00 
and set the MTU field to Automatic

Select "Connect Automatically" and then select "Apply"

Restart your machine and the DSL Extreme wired connection should start right up.
GOOD LUCK!

---

### Post by arundutta on 2011-08-10
I have ubuntu 10.4 and broadband pppoe connection. But cannot connect to internet. Trying to open mozilla tells me server not found.sudo pppoeconf tells me access concentrator of your provider didnot respond. pls someone help!


Here are output of some commands that i tried using from google.
~$ ifconfig 

eth0      Link encap:Ethernet  HWaddr f0:4d:a2:48:21:b8  
          inet6 addr: fe80::f24d:a2ff:fe48:21b8/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:293 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1260 (1.2 KB)  TX bytes:27778 (27.7 KB) 
          Interrupt:30 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB) 

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:804 (804.0 B)

---

### Post by whatthefunk on 2011-08-10
If the above doesnt work, try doing it in the command line.  Open a terminal and type 

```
pppoeconf
```

Follow the instructions and you should be ready to go.

---

