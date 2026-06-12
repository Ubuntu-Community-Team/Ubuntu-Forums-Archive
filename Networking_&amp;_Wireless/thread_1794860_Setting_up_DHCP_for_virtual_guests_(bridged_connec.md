---
title: "Setting up DHCP for virtual guests (bridged connection)"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by YouBuntToo? on 2011-07-01
Hi all,

I have two hosts, each with a few virtual guests. I want the guests to be able to communicate with each other. To do this I set up a network bridge (br0). This works fine as long as I just assign the guests a static IP address. However, I need the guests to be assigned an IP within a particular range.

I have dnsmasq on my host (ubuntu 11.04) and the guests. How should I set up my dnsmasq.conf file so that this works? What else do I need to do? I just don't understand how to tell the host to assign IPs to a specific interface and all that.

Thanks.

---

