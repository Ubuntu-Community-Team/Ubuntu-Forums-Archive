---
title: "Detecting if an ubuntu system is connected to the network"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by barantamer on 2009-04-21
Hello,

I am trying to detect if my network is up and i have an internet connection.
I have been reading about dbus, but i couldnt find enough materials to accomplish what i want. 

Any idea on this subject would be appriciated 

Thanks

---

### Post by lloyd_b on 2009-04-21
> **barantamer said:**
> Hello,

I am trying to detect if my network is up and i have an internet connection.
I have been reading about dbus, but i couldnt find enough materials to accomplish what i want. 

Any idea on this subject would be appriciated 

Thanks

It's relatively simple to write a script for this purpose```
#!/bin/bash

if ping -c 1 www.yahoo.com ; then
  echo "The Internet is available"
else
  echo "No Internet available"
fi
```
You can easily add other commands into the "then" clause of that script to perform certain actions if the Internet is there. 

Lloyd B.

---

### Post by barantamer on 2009-04-21
thanks for the quick reply,

I was wondering if i can do it independent from a remote server such as yahoo,google,etc.. 
Checking a flag or something in the operating system maybe ?

And i am thinking how pidgean or msn detects internet connection immediately?

---

### Post by Kareeser on 2009-04-21
Pidgin and msn detect an internet connection by trying to establish a connection to their host server... :)

So it's the same thing.

---

### Post by lloyd_b on 2009-04-21
> **barantamer said:**
> thanks for the quick reply,

I was wondering if i can do it independent from a remote server such as yahoo,google,etc.. 
Checking a flag or something in the operating system maybe ?

And i am thinking how pidgean or msn detects internet connection immediately?

You can test whether or not your machine is getting a valid IP address (which indicates that DHCP is working), but this only tells you that you have LAN connectivity.  The *only* way to verify Internet connectivity is a test such as the one I suggested.  After all, even if you have LAN connectivity, and you can reach your ISP, it doesn't automatically guarantee that you can reach the Internet (Your ISP could be having problems of their own).

Lloyd B.

---

### Post by barantamer on 2009-04-22
Thanks everybody i guess i am going to follow your way.

But i thought about an other way which doesn`t require a remote server. I want to hear your thoughts about it.

What if i take the output of ifconfig command and check for the keyword "Scope:link" which seems to be the difference between the results of ifconfig command when the computer is connected to the internet or not.

> eth4      Link encap:Ethernet  HWaddr 00:1f:e2:4e:d0:f8  
          inet addr:172.16.1.1  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fe4e:d0f8/64 [COLOR="Red"]Scope:Link[/COLOR]
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:528889 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:344663274 (328.6 MB)  TX bytes:24042389 (22.9 MB)
          Interrupt:220 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28389 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22615039 (21.5 MB)  TX bytes:22615039 (21.5 MB)

Any thoughts ?

---

### Post by lloyd_b on 2009-04-22
> **barantamer said:**
> Thanks everybody i guess i am going to follow your way.

But i thought about an other way which doesn`t require a remote server. I want to hear your thoughts about it.

What if i take the output of ifconfig command and check for the keyword "Scope:link" which seems to be the difference between the results of ifconfig command when the computer is connected to the internet or not.



Any thoughts ?

That isn't telling you anything out an *Internet* connection.  "Scope:Link" will appear regardless of what you're connected to, be it your ISP, or just your local network.

For example:```
eth0      Link encap:Ethernet  HWaddr 00:16:76:93:db:f3  
          inet addr:192.168.0.75  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe93:dbf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1197365 (1.1 MB)  TX bytes:225013 (225.0 KB)
```In this case, I do not connect *directly* to the internet, but just to my LAN.  I have to route through a gateway in order to reach the Internet.  The output from ifconfig doesn't change if I disconnect the DSL cable - my machine simply has no way to see if there's a valid internet connection other than actually testing it (such as by sending a ping).

A simpler way than "scraping" the data from ifconfig would be to check the values in "/var/run/network/ifstate" - if the interface (eth4, in your case) appears in this file, then that interface is up. 

Lloyd B.

---

