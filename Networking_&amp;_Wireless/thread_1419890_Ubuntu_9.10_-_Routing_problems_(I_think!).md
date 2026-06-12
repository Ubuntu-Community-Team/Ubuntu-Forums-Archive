---
title: "Ubuntu 9.10 - Routing problems (I think!)"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by chunk1970 on 2010-03-02
Hi All,

This is my first post here as I couldnt find an answer on here.

I'm running Ubunto 9.10 which is mainly used for running xbmc. 

My system is an Asrock Ion 330 (Dual core atom).

I have 
-built-in wireless Atheros AR9285 (Configured as master using Hostapd)
-ethernet connections which allows accesss to my entire network
-both of the above are bridged together as br0
-usb adsl modem Speedtouch 330. Configured and working.
-dhcp3 server dishing out ip's on my network.

I also have a wireless router that im currently looking to replace when i get this working.

So my problem.
-If i connect to my system by my wireless router(that im looking to replace) dhcp3 configures my ip-addresses accordingly. However if i try to connect through my wireless on Asrock 330 It connects but dhcp3 cannot assign any ip's for it.

What im looking for is a procedure for the following:
- what the routing should be when using my Asrock as a wireless/ethernet bridge with internet access via an attached usb modem. I have been looking for a soloution but have been confusing myself.

Any help would be very much appreciated.

---

### Post by Charly85551 on 2010-03-03
Hi chunk,
looks like your system is over-specified. Normally the routers have the role as DHCP-server. If you want it differently you need to a) switch off the DHCP-server in the router and b) assign an IP to the router either automatically via DHCP or static with a fixed IP which is normally the better approach since you need to tell all your other PC's the IP-address of your gateway & DNS-server = router IP. 
If you intend to get a new router and getting rid of the wireless then check first if it offers DHCP.
Sometimes it is better to give fixed IP-addresses (and faster for log-in) at least to some hardware. Most DHCP-servers allow for a range of fixed IP. (normally the router has something like: 192.168.1.1 (= Internet Gateway) and you can decide to make the range of 192.168.1.20 to 192.168.1.100 available for DHCP IP-allocations.
Your wireless router can still be re-assigned as an access point if you need so.
Hope you get something runnimg on this basis.;)
cheers
charly85551

---

