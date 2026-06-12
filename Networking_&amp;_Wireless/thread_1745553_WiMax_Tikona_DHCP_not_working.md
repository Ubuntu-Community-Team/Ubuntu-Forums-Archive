---
title: "WiMax Tikona DHCP not working"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by hansum_rahul on 2011-05-01
As of now, my WiMAX connection (Tikona) does not work. My setup is as follows:

[BaseStation on Terrace] 
||
||
||
ethernet cable
||
||
[adapter (power) for BS]
||
||
||
[My LAN card]

Now opening up a browser page would redirect to 1.254.254.254 which would authenticate me from login.tikona.in (providing a username/password based auth)... 

My LAN card works fine (in fact WiMAX worked out of the box too) and I can connect via DHCP on WinXP.

Here's a screenie from winxp :

[IMG]https://lh3.googleusercontent.com/_tmpxmncC43Y/Tb0e1ouTAcI/AAAAAAAAADw/CujVRVl4pJo/s800/123.JPG[/IMG]

Here's a traceroute from WinXP:
Tracing route to google-public-dns-a.google.com [8.8.8.8]
over a maximum of 30 hops:

  1    19 ms    15 ms    13 ms  113.193.16.1
  2    12 ms    14 ms    15 ms  113.193.5.113
  3    15 ms     *       12 ms  10.0.137.2
  4    18 ms     *       16 ms  121.241.219.65.static-kolkata.vsnl.net.in [121.2
41.219.65]
  5    14 ms    21 ms    12 ms  59.163.16.65.static.vsnl.net.in [59.163.16.65]
  6   158 ms     *       55 ms  121.242.217.13.static-kolkata.vsnl.net.in [121.2
42.217.13]
  7    56 ms    54 ms    55 ms  172.25.75.17
  8    54 ms    57 ms    54 ms  172.31.17.13
  9    54 ms    54 ms    52 ms  172.31.2.45

On Ubuntu Auto eth0 shows not connected... I tried deleting and adding a new connection with the required mac. Still not working

I tried forcing internet address with:

ifconfig eth0 <ip-address> netmask <netmask>

Got this:

inet addr:113.193.17.2 Bcast:113.193.31.255 Mask:255.255.240.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:21 Base address:0xd800
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:36 errors:0 dropped:0 overruns:0 frame:0
TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2755 (2.7 KB) TX bytes:2755 (2.7 KB)

And the route was:

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
113.193.16.0 0.0.0.0 255.255.240.0 U 0 0 0 eth0
0.0.0.0 113.193.16.1 0.0.0.0 UG 0 0 0 eth0

Still did not work.

Any pointers what I doing wrong?

NB: I tried with a LiveCD figuring my setup was messed up perhaps. Did not work.

---

### Post by hansum_rahul on 2011-05-02
Currently setup:
[CENTER]
[IMG]https://lh5.googleusercontent.com/_tmpxmncC43Y/Tb5lvfhRo3I/AAAAAAAAAD4/aRNKlWp9o0s/s800/1.png[/IMG]

[IMG]https://lh4.googleusercontent.com/_tmpxmncC43Y/Tb5lxTOMZqI/AAAAAAAAAD8/aTDy3vwz8yI/s800/2.png[/IMG]

[IMG]https://lh5.googleusercontent.com/_tmpxmncC43Y/Tb5l9suEu9I/AAAAAAAAAEA/I4u6l24WFXE/s800/Screenshot.png[/IMG][/CENTER]

---

