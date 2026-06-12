---
title: "DHCP Server Connected Devices"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by geoinc on 2012-03-01
I have the dhcp server set up and working.  How can I view connected devices by their mac address?  I used nmap and it only showed me a list of ip addresses.  I am looking for mac addresses and or device names.  Thanks.

---

### Post by Doug S on 2012-03-01
The dhcp server leases file contains the mac addresses and IP addresses and host names for the addresses it gives out from the pool.
 
see: /var/lib/dhcp3/dhcpd.leases
 
It does not seem to list any information if the address is assigned based on mac address (I just noticed, as on my system I have both a pool, for guests, and most IP addresses assigned based on MAC address.)
 
Hope this helps.

---

### Post by geoinc on 2012-03-01
Perfect.  Thanks!

---

