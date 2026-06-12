---
title: "Connection sharing problems under 12.04"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by Sam Lowry on 2012-08-16
Hi all,

I have a problem regarding connection sharing. 
Have Ubuntu 12.04 and two ethernet cards installed. 
The first one (eth1) is connected to the internet with 802.1x authentication, the second one (eth0) 
has a static IP 192.168.0.1 (set in network manager for IPv4). 
I connected a wireless router to eth0, set the LAN IP to 192.168.1.1 (so it doesn't interfere with the 
other network) and set WAN to be automatically set through DHCP.
Additionally, I installed Firestarter, checked 'connection sharing', set eth1 to be the internet connection 
and eth0 to be shared to local network.

Result:
- eth1 has internet connection
- Clients can see WLAN-Router under 192.168.1.1

Problem:
- eth1/eth0 and WLAN-Router can't see each other.

My question is: how does the router get a WAN? My first guess was that it has to come from eth1 
(the one connected to the internet). So I did a ```
dhclient -v eth1
``` but did not get any results.

What am I missing? Hope someone can help
Lowry

---

