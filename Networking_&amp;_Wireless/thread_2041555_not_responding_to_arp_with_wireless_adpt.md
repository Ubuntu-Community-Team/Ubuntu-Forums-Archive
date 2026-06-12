---
title: "not responding to arp with wireless adpt"
date: 2012-08-12
forum: Networking &amp; Wireless
---

### Post by gobo7 on 2012-08-12
brought up ubuntu server 12.04 x64 for the first time to test as an appliance. the nic is a usb wireless adapter (ar9271 chip.)  the wireless adapter is configured and authenticates with the ap.  the firewall has been disabled (ufw disable).

but, the arp table on the server is not being populated nor is the server responding to arp requests.  if the arp table is manually populated, connections are possible and the server responds to arp requests from the populated mac.

this is not seen on the wired port.  at first, i thought this might be an issue with the the ar9271 adapter. tested it on a slackware 13.37 box and the issue was not witnessed.  

does anyone have any suggestions?

---

