---
title: "im gona cry over spilled networking"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by fattyxyz on 2009-08-22
i got my linux machine connected to my network and its got a good connection of like 71% to 91% but when i tried going on firefox it kept saying it couldnt find the connection and just wont let me use the internet so is their a way to enable the internet or just fix this problem

im running ubuntu 8.04

---

### Post by DGortze380 on 2009-08-22
> **fattyxyz said:**
> i got my linux machine connected to my network and its got a good connection of like 71% to 91% but when i tried going on firefox it kept saying it couldnt find the connection and just wont let me use the internet so is their a way to enable the internet or just fix this problem

im running ubuntu 8.04

Need more information... how is the computer connected to the network? What does the rest of the network look like? Wireless router? Etc ...

Sounds like a DNS issue.

Can you post the output of the following:

```
ifconfig -a
```

---

### Post by fattyxyz on 2009-08-23
its connected with a network adapter edimax ew-7128g to be exact the router is a d-link i dont know the model exactly as for what the network looks like i dont know how to answer that question the output for ifconfig -a was:
and im sorry to say im much to new to linux to convert the odt file to something i can copy and paste into this reply but their were alot of error and failures is that helps at all

---

### Post by Crafty Kisses on 2009-08-23
> **fattyxyz said:**
> its connected with a network adapter edimax ew-7128g to be exact the router is a d-link i dont know the model exactly as for what the network looks like i dont know how to answer that question the output for ifconfig -a was:
and im sorry to say im much to new to linux to convert the odt file to something i can copy and paste into this reply but their were alot of error and failures is that helps at all

You can copy and paste from the terminal if that's what you're asking. So post the results of **ifconfig -a**. Once you have done that I'd also like to see the following:
```
route
```
That will tell me some information I need so I and others can help you out a bit.

---

### Post by fattyxyz on 2009-08-23
here are the results of route and ifconfig -a:
eth1      Link encap:Ethernet  HWaddr 00:13:d4:08:50:00   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:974 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:974 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:48700 (47.5 KB)  TX bytes:48700 (47.5 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:1f:1f:49:d9:21   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-1F-1F-49-D9-21-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
oem@freekbox:~$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 

hope this was right

---

### Post by dbalascak on 2009-08-23
Looks like none of the interfaces is getting an IP address.  Which interface is supposed to be the active one?

---

