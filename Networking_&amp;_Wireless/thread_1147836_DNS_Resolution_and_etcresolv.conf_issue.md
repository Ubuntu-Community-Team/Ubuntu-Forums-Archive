---
title: "DNS Resolution and /etc/resolv.conf issue"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by definingmoment on 2009-05-03
It appears as if /etc/resolv.conf still gets overwritten (in Jaunty) using PPTP VPN. THis was a known issue in previous versions of Ubuntu and still appears to be un-fixed. Does anyone know how to utilize DNS name resolution since /etc/resolv.conf is being constantly overwritten?

---

### Post by papangul on 2009-05-03
There is no point in manually editing the resolv.conf file, because it is supposed to get overwritten by design.

Have you tried to set the "prepend domain name servers" parameter in /etc/dhcp3/dhclient.conf? Mine looks like this:

prepend domain-name-servers 202.54.1.30, 208.67.222.222;

also restart either the networking or the machine immediately after editing the file

---

### Post by definingmoment on 2009-05-03
Does this work even using VPN. I'm fairly sure I've tried this. It's worked great until I connected to VPN and then my nameservers were not added to resolv.conf. Have you used it with both?

---

### Post by papangul on 2009-05-03
No I haven't used VPN but your resolv.conf won't change and will get overwritten(if it is supposed to change at all) until you have restarted the networking.

---

### Post by definingmoment on 2009-05-03
I just tried this in 8.10 with PPTP VPN, it seemed to work OK. Thanks for help!

---

