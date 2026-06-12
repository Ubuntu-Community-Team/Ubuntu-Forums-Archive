---
title: "network crashs - webserver slow"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by spindler on 2011-10-26
I recently upgraded my system from 11.04 to 11.10 and now my Internet connection is slow and crashes a lot.

I am using my Ubunut server as a webserver.  When I attempt to access my websites which are hosted on this computer  from a separate computer the download takes a very long time and often crashes.

I also attempted to upload flash for Mozilla and I could not because of the internet connection is down....Although I can surf the net via google.

I also cannot ping from the server.

I attempted to reset the wired connection (eth0) using the following commands a number of times but the connection still crashes.

sudo su
ifconfig eth0 down
dhclient -r
ifconfig eth0 down
dhclient

When I run ifconfig I get the following:

eth0      Link encap:Ethernet  HWaddr 00:15:c5:5e:ee:d8  
          inet addr:192.168.1.182  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe5e:eed8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:958956 (958.9 KB)  TX bytes:197756 (197.7 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49512 (49.5 KB)  TX bytes:49512 (49.5 KB)


Any idea how I can troubleshoot and repair this?

---

