---
title: "Smoothwall, router, WAP issues"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by antmenj on 2010-01-18
The setup goes like this:

ADSL model -->smoothwallbox (green zone) --> hub -->WAP~~~~ bridgemode ~~~~ WAP --> wifi router (DHCP turned off, wan port not used) --> computer.

The trouble is I can't access the config pages of the two WAPs or the wifi router.  These have been set to 192.168.1.10, 192.168.1.20 and 192.168.1.30.  Smoothwall is set to serve DHCP from 192.168.0.100 through to 192.168.0.200.  The network is working fine apart from being unable to use the config pages.

When I had the setup like this running in reverse I could see and use all config pages:

Cable modem --> wifi router (DHCP on, wan port used) --> WAP ~~~ bridge ~~~ WAP --> computer.

What am I doing wrong.........:confused:

---

