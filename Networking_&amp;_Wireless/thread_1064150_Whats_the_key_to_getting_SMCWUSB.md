---
title: "Whats the key to getting SMCWUSB"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by dwsdad on 2009-02-08
to work in 8.04?  I´ve tried ndiswrapper and the so called native drivers to work and still nothing.

lsusb shows:
Bus 004 Device 002: ID 083a:4505 Accton Technology Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

and lshw shows:
 *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:13:f7:8c:42:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g

I downloaded the drivers from the SMC site and all I get is errors while trying to compile them.

---

### Post by dwsdad on 2009-02-08
I finally got the ndiswrapper to work.  I had to go into WICD and tell it the interface was eth1, not wlan like it thought it was.  I made sure that ndiswrapper was set in there as well.

---

