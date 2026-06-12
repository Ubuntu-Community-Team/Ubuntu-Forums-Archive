---
title: "Can't locate the damage to network system"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by nigel@lucidata.com on 2011-11-21
10.10 running sweetly on Acer Aspire One D255 for many months. Somewhere along the line, I suspect an update, the WiFi no longer functions directly. The symptom is that it receives packets, you can watch the count go up, but does not respond specifically to ARP requests. It has obtained an IP by dhcp Ok and appears to have a good pyhsical connection but will not function until a wired ethernet connection is plugged in briefly and then unplugged. All is then fine. Any ideas?

---

### Post by JamieSK on 2011-11-22
When you first start-up does it work fine? Or does the problem still occur when you first start up?
 
I'm just wondering if its something to do with DHCP where the lease runs out on the current IP and then hangs. Have you tried releasing your IP address and renewing it when you get this problem?

---

### Post by nigel@lucidata.com on 2011-11-22
No it fails from the start. My router/DHCP server has a restricted pool for WiFi and always issues the same IP for what is the only (usually) WiFi device. All our other machines are hardwired and use static IPs in a laboratory environment. When I plug in an ethernet cable the eth1 interface has a static IP compatible with the other hosts. The lease time of the DHCP is 24 hours. Thanks for your comments. Nigel.

---

### Post by JamieSK on 2011-11-22
Just clarifying, does it work fine after it has been physically connected?

With that said, I don't know how much help I will be as I'm quite new to linux, I will try though ;) 

Mind doing a

```
ifconfig
```Before and after you have plugged in the ethernet cable and getting the wireless working and see if anything changed?

---

### Post by nigel@lucidata.com on 2011-11-28
Just to put on record the solution and to close the thread. 
The Routing table had become disordered so that the cable entry appeared first. So if the WiFi came up first, which is the usual case, it would try and use the first entry which was non-functioning. If the UTP connection was briefly brought up and dropped the routing table was correctly filled in and everything was OK from then on.
I think the problem might have occurred when struggling with the GUI of Network Manager which, while not wanting to be too critical, is a bit clunky and does not let (me at any rate ) one fill in all the fields, listed for a static IP address. Thanks for those showing an interest in my problem. Nigel.

---

