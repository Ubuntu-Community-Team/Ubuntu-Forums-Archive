---
title: "Firewall, Filter and VPN appliance in one box."
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2009-11-19
I'm thinking about linking several (10 to 14) internet networks (100 to 600 nodes each) together via a VPN into one domain. I'd like to create a linux box to fulfil the following roles; Firewall, Filter, and VPN appliance. This linux box would sit after the router and before the internet connectivity device.

These linux box could be one OS running all of the servers, or one HostOS with a seperate VirtualBox Machines for each server. But each box needs to get its configuration (filter and firewall) from one central location or share. Ease and central management.

Firewall 
pretty self explanitory for a linux box. Using firestarter or webmin GUI. Firestarter would require an X server also, but might be worth it for the ease of configuration.

Filter 
Using squid and dansguardian or ipcop. I've set up squid proxies and dansguardian before. I don't see this as being much of a problem. It would be nice to be a web cache and filter proxy at the same time.

VPN 
I don't know yet, maybe OpenSwan? Please suggest a VPN server or package. Preferably apt-get'able. But most importantly easy to configure. Preferably with a GUI through webmin or X.

Any other advice or foreseeable problems is also welcome.

---

### Post by dmizer on 2009-11-19
You're better off going with a gateway distribution. There are tons of these, here's a few suggestions (all of which can do everything you want):

ClarkConnect: [http://www.clarkconnect.com/](http://www.clarkconnect.com/)
Ungangle: [http://www.untangle.com/](http://www.untangle.com/)
Shorewall: [http://www.shorewall.net/](http://www.shorewall.net/)
eBox: [http://www.ebox-platform.com/](http://www.ebox-platform.com/) (this one is based on Ubuntu)
m0n0wall: [http://m0n0.ch/wall/](http://m0n0.ch/wall/)

Here's a bunch more: [http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

Most of those have very easy to use web interfaces.

---

