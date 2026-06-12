---
title: "Ethernet / DNS issue in Jaunty"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by beakdan on 2009-05-15
Hey folks-

First, let me point out that this may be a holdover from the issues involving NetworkManager in Intrepid.  I'd turned off NM, then tried to get it back, and it's possible I missed something, although I checked everything I could think of.

I'm trying to set up a static IP on my desktop, which is connected to my router via an ethernet cable (card is Atheros AR2413).  My main reason for wanting a static IP is to run Unison to backup and synchronize my laptop.

If I let NM make a connection using DHCP, it does so fine, and I can connect to both the local network and the internet with no issues.  I'll call this connection "Wired_1"

However, if I make a second connection, I'll call it "Manual" using manual setup with:
Address - 192.168.0.100
Netmask - 255.255.255.0
Gateway - 192.168.0.1

and using the MAC address that I see for eth0 when connected as Wired_1.

In this case (running the Manual connection), I do connect to my local network as address 192.168.0.100, just as I'd like.  From my laptop, I can ping my desktop at the address above.  I can also ping my laptop from my desktop.  On one level, there's not a real problem, since I can successfully run Unison at this point.

However, I can't browse with Firefox.  I did some more checking and found that I can't ping google.com : the response is "unknown host google.com"

I -CAN- ping 209.85.171.100 (this being the ip address for google.com).

So, my thought is that this has something to do with the DNS lookup, but am not sure how to proceed.  Any advice appreciated.

Dan

---

### Post by beakdan on 2009-05-15
ifconfig results for "Wired_1" connection:

eth0      Link encap:Ethernet  HWaddr 00:13:8f:e7:d9:ba  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fee7:d9ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:138911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:205989229 (205.9 MB)  TX bytes:5885338 (5.8 MB)
          Interrupt:23 Base address:0x2a00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22162 (22.1 KB)  TX bytes:22162 (22.1 KB)


ifconfig results for "Manual" connection

eth0      Link encap:Ethernet  HWaddr 00:13:8f:e7:d9:ba  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fee7:d9ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:139015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:206035712 (206.0 MB)  TX bytes:5914908 (5.9 MB)
          Interrupt:23 Base address:0x2a00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:335 errors:0 dropped:0 overruns:0 frame:0
          TX packets:335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27554 (27.5 KB)  TX bytes:27554 (27.5 KB)

---

### Post by beakdan on 2009-05-15
a-ha! A friend of mine helped me sort this out...

the file /etc/resolve.conf was empty, so the connection didn't know who to ask for DNS results.

I added "nameserver 198.168.0.1", thus telling it to ask the router, and then rebooted.  It seems to be fine now, and even held the IP address on reboot, so I guess the NM bug is fixed.

---

### Post by chili555 on 2009-05-15
I am sure you did it correctly, since it works correctly, but just for the benefit of the future searchers, it is */etc/resolv.conf*, with no 'e.'

When an Ubuntian sets up a static IP address, the system expects you to supply the address, broadcast, gateway *and* DNS addresses. Many of us, including me, have forgotten the DNS part!

---

