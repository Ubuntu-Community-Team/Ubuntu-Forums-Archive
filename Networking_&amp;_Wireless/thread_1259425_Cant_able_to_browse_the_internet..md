---
title: "Cant able to browse the internet."
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by karthick87 on 2009-09-06
My plog command says that i am connected to internet.But when i enter the page it keeps loading forever..

I have tried the ping command,it gives me the reply but the page keeps loading..
karthick@karthick-desktop:~$ ping -c 4 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=51 time=293 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=51 time=293 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=51 time=295 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=51 time=295 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 293.202/294.310/295.133/0.903 ms

---

### Post by vineeth_vijay on 2009-09-06
Please try clearing your cookies..
And then reload the page..

---

### Post by karthick87 on 2009-09-06
I have tried,but still i have the problem

---

### Post by uylug on 2009-09-06
Is firefox able to resolve the host name? Have you tried browsing by ip address?

---

### Post by DJonsson2008 on 2009-09-06
one of the best remedies for this i've heard on this forum is
to boot with an ubuntu live disk and see if you can browse
the net with that.  then for starters open up terminal 
and compare the ifconfig with live disk and with the
machine in question.

---

### Post by uylug on 2009-09-06
You can clear your firefox data by doing:

```
mv .mozilla .mozbck
```

Start firefox with default settings:

```
firefox
```

And revert your settings by doing:
```
mv .mozbck .mozilla
```

---

### Post by karthick87 on 2009-09-06
Yes it works fine if i give the ip address..

---

### Post by uylug on 2009-09-06
> **getyourkarthick said:**
> Yes it works fine if i give the ip address..

Okay, then Firefox is not resolving domain names.

Then go ahead, reset your firefox settings using the code I gave you, and then start firefox and go into edit -> preferences -> advanced -> Network -> Settings and see whether you can get it to work by messing with those settings.

---

### Post by shredder12 on 2009-09-06
if your terminal can resolve IP address then firefox should not have problems with that..
it could be an mtu issue..
try this [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

---

### Post by karthick87 on 2009-09-07
I have changed my MTU value but the problem not yet solved.

**ifconfig:**
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:ab:17:70  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:feab:1770/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST ** MTU:1492 ** Metric:1
          RX packets:1101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1050636 (1.0 MB)  TX bytes:138094 (138.0 KB)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1425592 (1.4 MB)  TX bytes:1425592 (1.4 MB)

---

### Post by shredder12 on 2009-09-07
Well, I believe firefox is not able to resolve hostnames

So, try this.. open your firefox.. in the url bar type "about:config"

and type "network.dns.IPv6.disable" in the filter bar..
double click it and change the value from false to true..

then restart your firefox.. and see if your issue is solved..

I am suggesting this because i think IPv6 is enabled by default on your system..
You can even try disabling IPv6
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
lets see if it helps..

---

