---
title: "Cannot use Deluge when bound to Ipredator VPN"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by bhunji on 2012-05-16
I created a vpn by using 



$ nslookup vpn.ipredator.se 



to  find the ipredator ip address to use (eg 93.182.174.130)  - I didn' t  use "vpn.ipredator.se" as the Gateway in the Network Manager applet,  because that didn't work on 10.04.
 

  The VPN works fine, but when I try to bind deluge to the VPN ip  address (via Edit -> Preferences -> Network -> Interface) I get this tracker  error:


  "openbittorrent.com: Error: Cannot assign requested address", and  there are no connections. Other applications still work over the VPN.



  When I remove the ip address from the Interface box and click Apply , deluge works fine.


I am using 12.04 (Classic) and I had the same problem with 10.04

Deluge 1.3.5


I'm only after a way to stop my ip address leaking when the VPN cuts out. This seems like the simplest method (if it would work:confused:),  but I'm open to other methods. I'm not comfortable with ip tables, but  from what I can gather I can assign a range of ports for deluge to use,  and then use GUFW to only allow traffic on those ports to the ipredator  server. 


I guess this is a deluge bug, or a quirk of how trackers work. Anyone else had the same issues? Any ideas for troubleshooting?

---

### Post by bhunji on 2012-05-17
If your vpn connects to 93.182.168.2

The Deluge interface must be 93.182.168.2*

edit: This doesn't work.

Neither does setting both the VPN Gateway and deluge interface to  vpn.ipredator.se - deluge still runs when the vpn disconnects, but only  connects to peers who are also using ipredator.

There seems to be no easy way to do this (could be done by using iptables or editing routes in /etc/ppp).

Switched to qbittorrent instead. Advanced tab in options lets you set the network interface to ppp0. Seems to work.

---

