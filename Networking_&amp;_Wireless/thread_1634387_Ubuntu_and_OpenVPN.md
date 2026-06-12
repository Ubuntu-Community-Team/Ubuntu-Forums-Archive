---
title: "Ubuntu and OpenVPN"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by baker126 on 2010-11-30
Quick and probably stupid question...

I want to connect remotely to a machine using OpenVPN.  Our work network is set up like this:   Internet ---> Work Gateway/Router ---> Pfsense Firewall --> Internal Machine

I want to access the internal through the Pfsense Firewall.  I already have Pfsense configured as the VPN server so I am hoping to access the machine on my little subnet through the firewall box.  We have a Dynamic IP address, but I wrote a script that updates me when ever our public IP address changes and provides the new one.  

How to phrase the "Gateway" descriptor in the Network Manager configuration which would allow me pass through our company's router to my firewall?  75.xxx.xxx.xxx: hostname?

Thanks.

---

