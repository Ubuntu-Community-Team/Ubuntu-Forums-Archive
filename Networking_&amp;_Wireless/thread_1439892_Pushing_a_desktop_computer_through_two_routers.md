---
title: "Pushing a desktop computer through two routers"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by espressobeanie on 2010-03-26
Hi,

I have two routers. One is a Verizon ProLine and the other is a Dlink. My setup is myComputer-Dlink-ProLine-Internet. I'm trying to get port 80 requests from the outside, access my http server on myComputer. I tried port forwarding on both routers, but that didn't work. I also tried to make the ProLine treat the Dlink as a DMZ, but that still doesn't work. Can anyone help?

---

### Post by Iowan on 2010-03-27
I'm not really familiar with either router - but your thread looked lonely...
I'm curious why two routers... but forwarding should work anyway. I remember a similar thread (but , of course, can't remember where). You're fordwarding from first router to 2nd router's IP address - then from 2nd router to server?

---

### Post by 98cwitr on 2010-03-27
Treat the Dlink as a bridge:

skip plugging into the WAN port on the dlink and use port 2, 3, or 4

turn off DHCP (and any other protocols that you can configure) and set a static IP on the dlink. Let the verizon gateway do all the work. 

Should work after that.

---

### Post by espressobeanie on 2010-03-27
Verizon Internet Service comes with a router built into their modem and I use a second for wireless access. I have forwarded port 80 to the 2nd router which forwards it to my computer on a specific ip address. Still can't seem to connect from the outside to it. 

98cwitr, thanks. I'll try that and see what I come up with.
Note: I do have an issue with setting it as a static ip address because it requires a primary and secondary DNS address that I have no clue how to get.

---

### Post by pbpersson on 2010-03-27
> **espressobeanie said:**
> 
Note: I do have an issue with setting it as a static ip address because it requires a primary and secondary DNS address that I have no clue how to get.

You would connect a computer to the Verizon router and get the DNS addresses there, temporarily bypassing the second router.  

I have the same setup here.....well, no I don't.....my Linksys router was acting weird - it would not hand out IP addresses any more - so I turned off the DHCP and it is acting as a switch and wireless access point.  I have a Linux machine acting as the firewall and DHCP server.

---

