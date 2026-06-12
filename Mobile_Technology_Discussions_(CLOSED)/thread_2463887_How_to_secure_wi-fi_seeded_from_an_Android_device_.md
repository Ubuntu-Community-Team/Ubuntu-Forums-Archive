---
title: "How to secure wi-fi seeded from an Android device to an Ubuntu laptop"
date: 2021-06-20
forum: Mobile Technology Discussions (CLOSED)
---

### Post by smith73 on 2021-06-20
I use wifi seeded from an Android Samsung phone via hotspot to an Ubuntu laptop
and may need to make some payments via this wifi connection. I never make payments 
via smartphone wifi, becasue I think that Android's (or my specific smartphone's) security is crappy.

How can I secure the Android wi-fi connection used by Ubuntu?
Or how to check and secure the Android phone itself?

I was thinking to install a VPN server on an Ubuntu machine hosted by upcloud.com,
as recommended by Average Linux User. But it is unclear how to use it for wifi connection
and Android. Then another Linux user told that VPNs are mainly useful for internet access
in public wifi hotspots like hotels and airports. Do I need a VPN in this case?

I have another Xiaomi Redmi smartphone with some "second space" functionality
for security, but also rarely use wifi via it, because it closes an email opened in the browser
which I need to be opened constatnly. Maybe it's better than Android?

---

### Post by TheFu on 2021-06-20
All wifi is non-secure. We learned that a few months ago. Every wifi standard from 1998 including wifi-6 have security problems.  That means the only way to secure wifi is to use a VPN, network authentication via a Radius server is not sufficient.

I've had my home wifi on a different subnet for about 15 yrs and used a vpn to cross into the more secured wired subnet most of this time.  All the IoT stuff sits on the non-secure network. It cannot be trusted.  That includes all tablets and phones.  VPN or they don't get a connection to any sensitive stuff.  A wifi only laptop has to use a VPN just like android devices too.  Never trust wifi.

[https://www.consumer.ftc.gov/articles/how-safely-use-public-wi-fi-networks](https://www.consumer.ftc.gov/articles/how-safely-use-public-wi-fi-networks)
[https://arstechnica.com/gadgets/2021/05/farewell-to-firewalls-wi-fi-bugs-open-network-devices-to-remote-hacks/](https://arstechnica.com/gadgets/2021/05/farewell-to-firewalls-wi-fi-bugs-open-network-devices-to-remote-hacks/)
[https://scitechdaily.com/new-vulnerabilities-in-wi-fi-security-revealed/](https://scitechdaily.com/new-vulnerabilities-in-wi-fi-security-revealed/)

Be careful out there.

---

