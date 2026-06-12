---
title: "seeing wireless, says connected, can't view any pages"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by mel_jensen on 2010-01-18
Hi, and thanks in advance for whatever help you can give me.  I am new to Ubuntu but went through the troubleshooting guide in documentation.  With its help, I was able to get my wireless network set up and recognized by my computer. It is even saying it is connected.  However, when I try to access a page (in firefox, since that is all I have installed right now) I'm getting nowhere.  I tried pinging to both my  network and google in the terminal, and that works fine.  I also disabled ipv6 as suggested in the troubleshooting guide but that didn't seem to help. 
Does anyone have any other suggestions that I can try?
thanks!
mel

---

### Post by phiro1 on 2010-01-19
Hey try this change your mtu rates to 1496 reconect or reboot and try if its works and get ifconfig rates in terminal that we can see what is the problem if my solution not worked thnx!

---

### Post by mel_jensen on 2010-01-19
looks like I'm already there, here is the output from ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0f:20:c9:13:e7  
          inet addr:10.150.83.105  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20f:20ff:fec9:13e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:23886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15766 errors:1 dropped:0 overruns:1 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:28058926 (28.0 MB)  TX bytes:2460118 (2.4 MB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:640 (640.0 B)  TX bytes:640 (640.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:55:ed:4a  
          inet addr:10.150.83.106  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::290:4bff:fe55:ed4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:7831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2725079 (2.7 MB)  TX bytes:34225 (34.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-55-ED-4A-35-35-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by mel_jensen on 2010-01-19
[INDENT]someone also suggested that I try using wicd instead of network manager.  I tried that this morning, but ultimately I'm getting the same problem.  I'm "connected" to the wireless network and am able to ping but not able to get either browser (I also tried with chrome, just for the heck of it) to read or display pages.  
thanks for your help,
mel
[/INDENT]

---

### Post by Iowan on 2010-01-19
> **mel_jensen said:**
>  I'm "connected" to the wireless network and am able to ping but not able to get either browser  Ping by name, IP or either? Valid nameservers in */etc/resolv.conf*?

---

### Post by phiro1 on 2010-01-25
hey sory that i cant write back erlyer but i dont knowe why the heck are your mtu rates not 1500 this is set auto by instaling linux 
hawe you try to get your mtu rates on 1496

---

